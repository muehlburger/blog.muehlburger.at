+++
categories = ["Android", "Computer Science", "Programming"]
date = "2011-08-26T09:17:35+00:00"
dsq_thread_id = ["396398593"]
tags = ["Android Market", "HTTP", "JSON", "Latitude", "spritpreise", "spritpreisrechner.at"]
title = "[spritpreisrechner.at] – Apps entwickeln"
url = "/2011/08/spritpreisrechner-at-apps-entwickeln/"

+++
Vor kurzem wurde in Österreich der <a title="E-Control Spritpreisrechner" href="http://spritpreisrechner.at/" target="_blank">Spritpreisrechner der E-Control</a> offiziell der Öffentlichkeit vorgestellt. Es hat nicht lange gedauert, bis auch die ersten Android App Entwickler die Seite zu nutzen versuchten. So finden sich derzeit im Android Market schon einige <a title="Android Market Spritpreisrechner Apps" href="https://market.android.com/search?q=spritpreisrechner&so=1&c=apps" target="_blank">Spritpreisrechner Apps</a>.

Ich habe mir einmal das Datenformat angesehen, welches die Website spritpreisrechner.at für die Abfrage der Spritdaten benutzt. Es ist eigentlich ganz einfach:

Es werden per HTTP POST Request Anfragen an <a title="http://spritpreisrechner.at/espritmap-app/GasStationServlet" href="http://www.spritpreisrechner.at/espritmap-app/GasStationServlet" target="_blank">http://www.spritpreisrechner.at/espritmap-app/GasStationServlet</a> geschickt. Wichtig ist dabei der Parameter "data" der natürlich mit Werten (Längen- und Breitengraden bzw. einen Suchstring) initialisiert werden muss.

Beispielsweise könnte man folgenden cURL Aufruf ausführen (die Daten in "data" sind url-encoded"):

```
curl -d "data=%5B%22Graz%22%2C%22DIE%22%2C15.414262484145%2C47.057105360725%2C15.494085024429%2C47.08048974931%5D" http://www.spritpreisrechner.at/espritmap-app/GasStationServlet
```

Der HTTP Request Header sieht konkret folgendermaßen aus:

```
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
data:["","DIE",15.409674251128,47.051201316374,15.489496791403,47.074588294516]
Response Headersview source
Connection:Keep-Alive
Content-Type:text/html;charset=UTF-8
Date:Fri, 26 Aug 2011 08:27:11 GMT
Keep-Alive:timeout=4, max=150
Transfer-Encoding:chunked
```

Der Parameter "data" enthält einen JSON String der mit folgenden Werten befüllt wird:

```json
[
  "",
  "DIE",
  15.414258888907,
  47.057106335865,
  15.494081429191,
  47.080490724022
]
```

Hier die Beschreibung der einzelnen Felder:

```
[
"", => Ort (Tankstellen werden in der Nähe dieses Ortes gesucht) **Update:** Vielen Dank an Andreas Stütz!: Dieser Parameter gibt an, ob auch geschlossene Tankstellen angezeigt werden sollen ("checked") oder nicht ("")
"DIE", => Treibstoffart: "DIE" oder "SUP" (Diesel oder Super 95)
15.414258888907, => Longitude 1 (Längengrad)
47.057106335865, => Latitude 1 (Breitengrad)
15.494081429191, => Longitude 2 (Längengrad)
47.080490724022 => Latitude 2 (Breitengrad)  
]
```

Longitude 1 und Latitude 1 geben Koordinaten der linken unteren Ecke, Longitude 2 und Latitude 2 die Koordinaten der oberen rechten Ecke an. Das so aufgespannte Rechteck definiert den sichtbaren Bereich auf der Google Maps Karte. Im Zentrum sollte sich sinnvollerweise die aktuelle Position befinden. Innerhalb des sichtbaren Bereiches werden die 5 billigsten Tankstellen mit den dazugehörigen Spritpreisen angezeigt. Um das Rechteck aufzuspannen kann man sich in Android folgendermaßen behelfen:

1. Aktuelle Position mittels Android LocationManager ermitteln
  
2. Mittels der aktuellen Position und der Methoden <a title="getLongitudeSpan()" href="http://code.google.com/intl/de-DE/android/add-ons/google-apis/reference/com/google/android/maps/MapView.html#getLongitudeSpan()" target="_blank">getLongitudeSpan()</a> und <a title="getLatitudeSpan()" href="http://code.google.com/intl/de-DE/android/add-ons/google-apis/reference/com/google/android/maps/MapView.html#getLatitudeSpan()" target="_blank">getLatitudeSpan()</a> die rechte obere und die linke untere Ecke berechnen und anschließend
  
3. Parameter "data" mit den ermittelten Werten befüllen und HTTP Post Request abschicken.

Wird der oben beschriebene HTTP Request ausgeführt, bekommt man als HTTP Response einen JSON String, der wie folgt aufgebaut ist:

```json
[
  {
    "kredit":true,
    "self":true,
    "spritPrice":[
      {
        "amount":"1.262",
        "datAnounce":"Thu Aug 25 17:45:55 CEST 2011",
        "gasStationId":"7766",
        "errorItems":[

        ],
        "errorCode":0,
        "datValid":1314287155000,
        "spritId":"DIE"
      }
    ],
    "automat":false,
    "city":"Graz",
    "open":true,
    "distance":1.32,
    "postalCode":"8010",
    "    gasStationId":7766,
    "errorItems":[

    ],
    "priceSearchDisabled":false,
    "longitude":"15.4509774",
    "    payMethod":"UTA",
    "mail":"",
    "gasStationName":"Turmöl",
    "fax":"433164751524",
    "    clubCard":"",
    "openingHours":[
      {
        "beginn":"06:00",
        "day":{
          "dayLabel":"Feiertag",
          "order":8,
          "errorItems":[

          ],
          "errorCode":0,
          "day":"FE"
        },
        "end":"22:00"
      },
      {
        "beginn":"05:00",
        "day":{
          "dayLabel":"Dienstag",
          "order":2,
          "errorItems":[

          ],
          "errorCode":0,
          "day":"DI"
        },
        "end":"23:00"
      },
      {
        "beginn":"05:00",
        "day":{
          "dayLabel":"Montag",
          "order":1,
          "errorItems":[

          ],
          "errorCode":0,
          "day":"MO"
        },
        "end":"23:00"
      },
      {
        "beginn":"05:00",
        "day":{
          "dayLabel":"Freitag",
          "order":5,
          "errorItems":[

          ],
          "errorCode":0,
          "day":"FR"
        },
        "end":"23:00"
      },
      {
        "beginn":"06:00",
        "day":{
          "dayLabel":"Samstag",
          "order":6,
          "errorItems":[

          ],
          "errorCode":0,
          "day":"SA"
        },
        "end":"22:00"
      },
      {
        "beginn":"06:00",
        "day":{
          "dayLabel":"Sonntag",
          "order":7,
          "errorItems":[

          ],
          "errorCode":0,
          "day":"SO"
        },
        "end":"22:00"
      },
      {
        "beginn":"05:00",
        "day":{
          "dayLabel":"Mittwoch",
          "order":3,
          "errorItems":[

          ],
          "errorCode":0,
          "day":"MI"
        },
        "end":"23:00"
      },
      {
        "beginn":"05:00",
        "day":{
          "dayLabel":"Donnerstag",
          "order":4,
          "errorItems":[

          ],
          "errorCode":0,
          "day":"DO"
        },
        "end":"23:00"
      }
    ],
    "access":"",
    "url":"",
    "serviceText":"ShoprnBistrornWaschanlagernSB-LanzenwäschernDiesel-Schnellläuferrn",
    "maestro":true,
    "companionship":false,
    "address":"Conrad.-v.Hötzendorfstr. 135 ",
    "club":false,
    "errorCode":1,
    "service":false,
    "latitude":"47.0510643",
    "bar":true,
    "telephone":"43316475152",
    "gasStationInternalId":"CvH"
  }
]
```

Einen Parser für diesen JSON String zu schreiben, dürfte nicht allzu schwer sein. 🙂 Das war auch schon alles um eine App für spritpreisrechner.at entwicklen zu können. Eigentlich ziemlich einfach. Was meint ihr? Freu mich auf Kommentare und Anregungen!