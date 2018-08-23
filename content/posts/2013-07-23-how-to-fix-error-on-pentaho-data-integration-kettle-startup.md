---
title: How to fix error on Pentaho Data Integration (Kettle) startup
author: Herbert Mühlburger
type: post
date: 2013-07-23T07:48:40+00:00
url: /2013/07/how-to-fix-error-on-pentaho-data-integration-kettle-startup/
bitcointips_address:
  - 19NpYWYxxBGcYU4KwffxFj3Ltv4yZe97q5
categories:
  - Business Intelligence
  - Computer Science
  - HowTo
  - Kettle
  - Pentaho
tags:
  - BI
  - Business Intelligence
  - Data Integration
  - Kettle
  - PDI
  - Pentaho

---
Howto fix startup error of <a title="Pentaho Data Integration" href="http://kettle.pentaho.com/" target="_blank">Pentaho Data Integration</a> (Kettle) on CentOS 6? You just need to modify the spoon.sh startup script after downloading and unzipping Pentaho Data Integration. The modification updates the Java runtime options for Kettle to startup properly. Therefore open

[code language=&#8221;bash&#8221;]spoon.sh[/code]

and change the end of the file in the following way:

[code language=&#8221;bash&#8221;]
  
\# \***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***
  
\# \*\* Set java runtime options \*\*
  
\# \*\* Change 512m to higher values in case you run out of memory \*\*
  
\# \*\* or set the PENTAHO\_DI\_JAVA_OPTIONS environment variable \*\*
  
\# \***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***

if [ -z "$PENTAHO\_DI\_JAVA_OPTIONS" ]; then
  
PENTAHO\_DI\_JAVA_OPTIONS="-Xmx512m -XX:MaxPermSize=256m"
  
fi

OPT="$OPT $PENTAHO\_DI\_JAVA\_OPTIONS -Djava.library.path=$LIBPATH -DKETTLE\_HOME=$KETTLE\_HOME -DKETTLE\_REPOSITORY=$KETTLE\_REPOSITORY -DKETTLE\_USER=$KETTLE\_USER -DKETTLE\_PASSWORD=$KETTLE\_PASSWORD -DKETTLE\_PLUGIN\_PACKAGES=$KETTLE\_PLUGIN\_PACKAGES -DKETTLE\_LOG\_SIZE\_LIMIT=$KETTLE\_LOG\_SIZE_LIMIT -Dorg.eclipse.swt.browser.XULRunnerPath=/dev/null"
  
\# \***\***\***\***\***
  
\# \*\* Run&#8230; \*\*
  
\# \***\***\***\***\***
  
"$\_PENTAHO\_JAVA" $OPT $STARTUP -lib $LIBPATH "${1+$@}"
  
[/code]

Everything I did was appending

[code language=&#8221;bash&#8221;]-Dorg.eclipse.swt.browser.XULRunnerPath=/dev/null"[/code]

to the

[code language=&#8221;bash&#8221;]OPT[/code]

part as described in ticket <a title="TDI-24139" href="https://jira.talendforge.org/browse/TDI-24139?focusedCommentId=254634&page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-254634" target="_blank">TDI-24139</a>.