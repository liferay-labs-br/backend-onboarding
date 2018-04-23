---
title: "Eclipse"
description: "This section shows some tips related with the Eclipse IDE."
layout: "tips"
icon: ""
weight: 3
---

###### {$page.description}

<article id="1">

## Eclipse crashing?
1. Access ' Eclipse -> Content -> Eclipse -> eclipse.ini '.
2. Edit the file on the line that contains 'Xms' and ' Xmx' with the amount of space.
   - **E.g.:** Xms4G.

</article>

<article id="2">

## Problems getting access to debug mode in eclipse?
1. Check your **setenv.sh** file located in the bin folder of the tomcat.
2. Make sure the contents of the file match the text below:

```
CATALINA_OPTS="$CATALINA_OPTS -Dfile.encoding=UTF8 -Djava.net.preferIPv4Stack=true  -Dorg.apache.catalina.loader.WebappClassLoader.ENABLE_CLEAR_REFERENCES=false -Duser.timezone=GMT -Xdebug -Xrunjdwp:transport=dt_socket,address=8000,server=y,suspend=n"
JMX_OPTS="-Dcom.sun.management.jmxremote -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.port=8099 -Dcom.sun.management.jmxremote.ssl=false"

CATALINA_OPTS="${CATALINA_OPTS} ${JMX_OPTS}"

if [ "$1" = "jacoco" ]
then
    JACOCO_OPTS="-javaagent:/YOUR_PATH/bundles/liferay-portal/tomcat-8.0.32/bin/jacocoagent.jar=destfile=/YOUR_PATH/liferay-portal/jacoco/liferay-jacoco.exec,excludes=,includes=*,output=file,append=true"
    CATALINA_OPTS="${CATALINA_OPTS} ${JACOCO_OPTS}"
    shift
fi

CATALINA_OPTS="${CATALINA_OPTS} -javaagent:/YOUR_PATH/liferay-portal/lib/portal/aspectj-weaver.jar -Dorg.aspectj.weaver.loadtime.configuration=com/liferay/aspectj/aop.xml"

JPDA_ADDRESS="8000"
```
</article>

<article id="3">

## Indentation Help ?
1. Download plugin **Arbitrary Lines** .
2. Help -> Eclipse Marketplace
3. Access the advanced settings.
    - Eclipse -> Preferences -> General -> Editors -> Text Editors -> Arbitrary Lines -> Show Advanced Configuration
4. Enable checkbox 'character size override' .
5. Edit 'Override character width' field for 6.65.

</article>
