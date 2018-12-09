+++
aktt_notify_twitter = ["yes"]
aktt_tweeted = ["1"]
author = "Herbert Mühlburger"
bitcointips_address = ["16t3sVBxEVqyanTbfbvymr7WfAKJMwYerr"]
categories = ["Android", "Computer Science", "Programming"]
date = "2011-08-26T09:17:35+00:00"
dsq_thread_id = ["396398593"]
seo_follow = ["false"]
seo_noindex = ["false"]
tags = ["Android Market", "HTTP", "JSON", "Latitude", "spritpreise", "spritpreisrechner.at"]
title = "[spritpreisrechner.at] – Apps entwickeln"
type = "post"
url = "/2011/08/spritpreisrechner-at-apps-entwickeln/"

+++
Vor kurzem wurde in Österreich der <a title="E-Control Spritpreisrechner" href="http://spritpreisrechner.at/" target="_blank">Spritpreisrechner der E-Control</a> offiziell der Öffentlichkeit vorgestellt. Es hat nicht lange gedauert, bis auch die ersten Android App Entwickler die Seite zu nutzen versuchten. So finden sich derzeit im Android Market schon einige <a title="Android Market Spritpreisrechner Apps" href="https://market.android.com/search?q=spritpreisrechner&so=1&c=apps" target="_blank">Spritpreisrechner Apps</a>.

Ich habe mir einmal das Datenformat angesehen, welches die Website spritpreisrechner.at für die Abfrage der Spritdaten benutzt. Es ist eigentlich ganz einfach:

Es werden per HTTP POST Request Anfragen an <a title="http://spritpreisrechner.at/espritmap-app/GasStationServlet" href="http://www.spritpreisrechner.at/espritmap-app/GasStationServlet" target="_blank">http://www.spritpreisrechner.at/espritmap-app/GasStationServlet</a> geschickt. Wichtig ist dabei der Parameter &#8220;data&#8221; der natürlich mit Werten (Längen- und Breitengraden bzw. einen Suchstring) initialisiert werden muss.

Beispielsweise könnte man folgenden cURL Aufruf ausführen (die Daten in &#8220;data&#8221; sind url-encoded&#8221;):

[code language=&#8221;bash&#8221;]
  
curl -d &#8220;data=%5B%22Graz%22%2C%22DIE%22%2C15.414262484145%2C47.057105360725%2C15.494085024429%2C47.08048974931%5D&#8221; http://www.spritpreisrechner.at/espritmap-app/GasStationServlet
  
[/code]

Der HTTP Request Header sieht konkret folgendermaßen aus:

[code]
  
Request URL:http://www.spritpreisrechner.at/espritmap-app/GasStationServlet
  
Request Method:POST
  
Status Code:200 OK
  
Request Headersview source
  
Accept:\*/\*
  
Accept-Charset:ISO-8859-1,utf-8;q=0.7,*;q=0.3
  
Accept-Encoding:gzip,deflate,sdch
  
Accept-Language:de-DE,de;q=0.8,en-US;q=0.6,en;q=0.4
  
Connection:keep-alive
  
Content-Length:101
  
Content-Type:application/x-www-form-urlencoded
  
Host:spritpreisrechner.at
  
Origin:http://spritpreisrechner.at
  
Referer:http://spritpreisrechner.at/ts/map.jsp
  
User-Agent:Mozilla/5.0 (Macintosh; Intel Mac OS X 10\_7\_1) AppleWebKit/535.1 (KHTML, like Gecko) Chrome/13.0.782.215 Safari/535.1
  
X-Requested-With:XMLHttpRequest
  
Form Dataview URL encoded
  
data:[&#8220;&#8221;,&#8221;DIE&#8221;,15.409674251128,47.051201316374,15.489496791403,47.074588294516]
  
Response Headersview source
  
Connection:Keep-Alive
  
Content-Type:text/html;charset=UTF-8
  
Date:Fri, 26 Aug 2011 08:27:11 GMT
  
Keep-Alive:timeout=4, max=150
  
Transfer-Encoding:chunked
  
[/code]

Der Parameter &#8220;data&#8221; enthält einen JSON String der mit folgenden Werten befüllt wird:

[code]
  
data:[
  
&#8220;&#8221;, => <del>Ort (Tankstellen werden in der Nähe dieses Ortes gesucht)</del> **Update:** Vielen Dank an Andreas Stütz!: Dieser Parameter gibt an, ob auch geschlossene Tankstellen angezeigt werden sollen (&#8220;checked&#8221;) oder nicht (&#8220;&#8221;)
	  
&#8220;DIE&#8221;, => Treibstoffart: &#8220;DIE&#8221; oder &#8220;SUP&#8221; (Diesel oder Super 95)
	  
15.414258888907, => Longitude 1 (Längengrad)
	  
47.057106335865, => Latitude 1 (Breitengrad)
	  
15.494081429191, => Longitude 2 (Längengrad)
	  
47.080490724022 => Latitude 2 (Breitengrad)
  
]
  
[/code]

Longitude 1 und Latitude 1 geben Koordinaten der linken unteren Ecke, Longitude 2 und Latitude 2 die Koordinaten der oberen rechten Ecke an. Das so aufgespannte Rechteck definiert den sichtbaren Bereich auf der Google Maps Karte. Im Zentrum sollte sich sinnvollerweise die aktuelle Position befinden. Innerhalb des sichtbaren Bereiches werden die 5 billigsten Tankstellen mit den dazugehörigen Spritpreisen angezeigt. Um das Rechteck aufzuspannen kann man sich in Android folgendermaßen behelfen:

1. Aktuelle Position mittels Android LocationManager ermitteln
  
2. Mittels der aktuellen Position und der Methoden <a title="getLongitudeSpan()" href="http://code.google.com/intl/de-DE/android/add-ons/google-apis/reference/com/google/android/maps/MapView.html#getLongitudeSpan()" target="_blank">getLongitudeSpan()</a> und <a title="getLatitudeSpan()" href="http://code.google.com/intl/de-DE/android/add-ons/google-apis/reference/com/google/android/maps/MapView.html#getLatitudeSpan()" target="_blank">getLatitudeSpan()</a> die rechte obere und die linke untere Ecke berechnen und anschließend
  
3. Parameter &#8220;data&#8221; mit den ermittelten Werten befüllen und HTTP Post Request abschicken.

Wird der oben beschriebene HTTP Request ausgeführt, bekommt man als HTTP Response einen JSON String, der wie folgt aufgebaut ist:

[code]
  
[
    
{
      
&#8220;kredit&#8221;:true,
      
&#8220;self&#8221;:true,
      
&#8220;spritPrice&#8221;:[
        
{
          
&#8220;amount&#8221;:&#8221;1.262&#8243;,
          
&#8220;datAnounce&#8221;:&#8221;Thu Aug 25 17:45:55 CEST 2011&#8243;,
          
&#8220;gasStationId&#8221;:&#8221;7766&#8243;,
          
&#8220;errorItems&#8221;:[

],
          
&#8220;errorCode&#8221;:0,
          
&#8220;datValid&#8221;:1314287155000,
          
&#8220;spritId&#8221;:&#8221;DIE&#8221;
        
}
      
],
      
&#8220;automat&#8221;:false,
      
&#8220;city&#8221;:&#8221;Graz&#8221;,
      
&#8220;open&#8221;:true,
      
&#8220;distance&#8221;:1.32,
      
&#8220;postalCode&#8221;:&#8221;8010&#8243;,
      
&#8220;gasStationId&#8221;:7766,
      
&#8220;errorItems&#8221;:[

],
      
&#8220;priceSearchDisabled&#8221;:false,
      
&#8220;longitude&#8221;:&#8221;15.4509774&#8243;,
      
&#8220;payMethod&#8221;:&#8221;UTA&#8221;,
      
&#8220;mail&#8221;:&#8221;&#8221;,
      
&#8220;gasStationName&#8221;:&#8221;Turmöl&#8221;,
      
&#8220;fax&#8221;:&#8221;433164751524&#8243;,
      
&#8220;clubCard&#8221;:&#8221;&#8221;,
      
&#8220;openingHours&#8221;:[
        
{
          
&#8220;beginn&#8221;:&#8221;06:00&#8243;,
          
&#8220;day&#8221;:{
            
&#8220;dayLabel&#8221;:&#8221;Feiertag&#8221;,
            
&#8220;order&#8221;:8,
            
&#8220;errorItems&#8221;:[

],
            
&#8220;errorCode&#8221;:0,
            
&#8220;day&#8221;:&#8221;FE&#8221;
          
},
          
&#8220;end&#8221;:&#8221;22:00&#8243;
        
},
        
{
          
&#8220;beginn&#8221;:&#8221;05:00&#8243;,
          
&#8220;day&#8221;:{
            
&#8220;dayLabel&#8221;:&#8221;Dienstag&#8221;,
            
&#8220;order&#8221;:2,
            
&#8220;errorItems&#8221;:[

],
            
&#8220;errorCode&#8221;:0,
            
&#8220;day&#8221;:&#8221;DI&#8221;
          
},
          
&#8220;end&#8221;:&#8221;23:00&#8243;
        
},
        
{
          
&#8220;beginn&#8221;:&#8221;05:00&#8243;,
          
&#8220;day&#8221;:{
            
&#8220;dayLabel&#8221;:&#8221;Montag&#8221;,
            
&#8220;order&#8221;:1,
            
&#8220;errorItems&#8221;:[

],
            
&#8220;errorCode&#8221;:0,
            
&#8220;day&#8221;:&#8221;MO&#8221;
          
},
          
&#8220;end&#8221;:&#8221;23:00&#8243;
        
},
        
{
          
&#8220;beginn&#8221;:&#8221;05:00&#8243;,
          
&#8220;day&#8221;:{
            
&#8220;dayLabel&#8221;:&#8221;Freitag&#8221;,
            
&#8220;order&#8221;:5,
            
&#8220;errorItems&#8221;:[

],
            
&#8220;errorCode&#8221;:0,
            
&#8220;day&#8221;:&#8221;FR&#8221;
          
},
          
&#8220;end&#8221;:&#8221;23:00&#8243;
        
},
        
{
          
&#8220;beginn&#8221;:&#8221;06:00&#8243;,
          
&#8220;day&#8221;:{
            
&#8220;dayLabel&#8221;:&#8221;Samstag&#8221;,
            
&#8220;order&#8221;:6,
            
&#8220;errorItems&#8221;:[

],
            
&#8220;errorCode&#8221;:0,
            
&#8220;day&#8221;:&#8221;SA&#8221;
          
},
          
&#8220;end&#8221;:&#8221;22:00&#8243;
        
},
        
{
          
&#8220;beginn&#8221;:&#8221;06:00&#8243;,
          
&#8220;day&#8221;:{
            
&#8220;dayLabel&#8221;:&#8221;Sonntag&#8221;,
            
&#8220;order&#8221;:7,
            
&#8220;errorItems&#8221;:[

],
            
&#8220;errorCode&#8221;:0,
            
&#8220;day&#8221;:&#8221;SO&#8221;
          
},
          
&#8220;end&#8221;:&#8221;22:00&#8243;
        
},
        
{
          
&#8220;beginn&#8221;:&#8221;05:00&#8243;,
          
&#8220;day&#8221;:{
            
&#8220;dayLabel&#8221;:&#8221;Mittwoch&#8221;,
            
&#8220;order&#8221;:3,
            
&#8220;errorItems&#8221;:[

],
            
&#8220;errorCode&#8221;:0,
            
&#8220;day&#8221;:&#8221;MI&#8221;
          
},
          
&#8220;end&#8221;:&#8221;23:00&#8243;
        
},
        
{
          
&#8220;beginn&#8221;:&#8221;05:00&#8243;,
          
&#8220;day&#8221;:{
            
&#8220;dayLabel&#8221;:&#8221;Donnerstag&#8221;,
            
&#8220;order&#8221;:4,
            
&#8220;errorItems&#8221;:[

],
            
&#8220;errorCode&#8221;:0,
            
&#8220;day&#8221;:&#8221;DO&#8221;
          
},
          
&#8220;end&#8221;:&#8221;23:00&#8243;
        
}
      
],
      
&#8220;access&#8221;:&#8221;&#8221;,
      
&#8220;url&#8221;:&#8221;&#8221;,
      
&#8220;serviceText&#8221;:&#8221;ShoprnBistrornWaschanlagernSB-LanzenwäschernDiesel-Schnellläuferrn&#8221;,
      
&#8220;maestro&#8221;:true,
      
&#8220;companionship&#8221;:false,
      
&#8220;address&#8221;:&#8221;Conrad.-v.Hötzendorfstr. 135 &#8220;,
      
&#8220;club&#8221;:false,
      
&#8220;errorCode&#8221;:1,
      
&#8220;service&#8221;:false,
      
&#8220;latitude&#8221;:&#8221;47.0510643&#8243;,
      
&#8220;bar&#8221;:true,
      
&#8220;telephone&#8221;:&#8221;43316475152&#8243;,
      
&#8220;gasStationInternalId&#8221;:&#8221;CvH&#8221;
    
}
  
]
  
[/code]

Einen Parser für diesen JSON String zu schreiben, dürfte nicht allzu schwer sein. 🙂 Das war auch schon alles um eine App für spritpreisrechner.at entwicklen zu können. Eigentlich ziemlich einfach. Was meint ihr? Freu mich auf Kommentare und Anregungen!