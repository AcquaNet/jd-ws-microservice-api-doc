# JD Atina microservices - Installation #

## Start JD Web Services Microservice / JDE Rest API Microservice ##

### Installation ###

Download [JD Docker Composer Files](http://157.245.236.175:8081/artifactory/libs-release/com/atina/jd-docker-files/1.0.0/jd-docker-files-1.0.0.zip) - latest release:

<pre class="center-column"> 
curl http://157.245.236.175:8081/artifactory/libs-release/com/atina/jd-docker-files/1.0.0/jd-docker-files-1.0.0.zip \
	--output jd-docker-files-1.0.0.zip     
</pre>
<p>&nbsp;<br></p>

Unzip JD Docker Composer Files (**jd-docker-files-1.0.0.zip**) downloaded in a temporal folder.

<pre class="center-column"> 
7z e jd-docker-files-1.0.0.zip    
</pre>
<p>&nbsp;<br></p>

### Configuration ###

Edit .env file and change the following values:

under **DNS_SERVERS** section inside jdeinterop.ini files to complete theses values:

<pre class="center-column"> 
7z e jd-docker-files-1.0.0.zip  #
# ====================================
# ETC/HOST
# ====================================
#
JDE_MICROSERVER_ENTERPRISE_SERVER_NAME=JDE-ENT
JDE_MICROSERVER_ENTERPRISE_SERVER_IP=1.1.1.1
JDE_MICROSERVER_ENTERPRISE_DB_NAME=JDE-DATABASE 
JDE_MICROSERVER_ENTERPRISE_DB_IP=2.2.2.2
</pre>
<p>&nbsp;<br></p>

### Create and Run JD Microservices ###

**Run following docker commands:**

<pre class="center-column"> 
docker-compose -f docker-compose-dist.yml up --no-start
</pre>
<p>&nbsp;<br></p>

**Copy files Configuration files and jars files into Container**

<pre class="center-column"> 
docker cp /tmp/build_jde_libs/JPS920 jd-atina-microserver:/tmp/jde/config
docker cp /tmp/build_jde_libs/jde-lib-wrapped-1.0.0.jar jd-atina-microserver:/tmp/jde
docker cp /tmp/build_jde_libs/StdWebService-1.0.0.jar jd-atina-microserver:/tmp/jde
</pre>
<p>&nbsp;<br></p>

**Run Containers**

<pre class="center-column"> 
docker-compose -f docker-compose-dist.yml start
</pre>
<p>&nbsp;<br></p>

**Check JD WS Microservice startup**

Check starting process for JD Atina WS Microservice

<pre class="center-column"> 
docker exec -it jd-atina-microserver cat /tmp/start.log
</pre>
<p>&nbsp;<br></p>

<pre class="center-column"> 
-SERVICE--------------------------------------------
   Name:  172.28.0.2
   Port:  8077
-REPOSITORY-----------------------------------------
   Customer:  http:157.245.236.175:8081/artifactory/libs-release
   Atina:     http:157.245.236.175:8081/artifactory/libs-release
-LIBRARIES------------------------------------------
   StdWebService Version  1.0.0
   jde-lib-wrapped Version 1.0.0
   JDEAtinaServer Version 1.0.0
-LICENSE--------------------------------------------
   Code:  demo
-MICROSERVER----------------------------------------
   JDE_MICROSERVER_TOKEN_EXPIRATION:  3000000
   JDE_MICROSERVER_ENTERPRISE_SERVER_NAME:  JDE-ENT
   JDE_MICROSERVER_ENTERPRISE_SERVER_IP:  522.21.33.261
   JDE_MICROSERVER_ENTERPRISE_DB_NAME:  JDE-DATABASE
   JDE_MICROSERVER_ENTERPRISE_DB_IP:  625.22.339.57
   JDE_MICROSERVER_MOCKING:  0
----------------------------------------------------
ADDITIONAL SCRIPT:
  127.0.0.1       localhost
  172.28.0.2      bcd05e8e5bd0
----------------------------------------------------
 Check log cat /tmp/jde/JDEConnectorServerLog/jd_atina_server_2021-11-18.0.log
</pre>
<p>&nbsp;<br></p>

At the end of the logs, you will the log that you need to check. Run the following docker command:

<pre class="center-column"> 
docker exec -it jd-atina-microserver cat /tmp/jde/JDEConnectorServerLog/jde_atina_server_2021-11-18.0.log
</pre>
<p>&nbsp;<br></p>

<pre class="center-column"> 
....
19:27:06.713 [main] INFO  c.acqua.jde.jdeconnectorserver.JDEConnectorServer - Iniciando JDE Service Impl...
19:27:06.891 [main] INFO  c.a.jde.jdeconnectorserver.server.JDERestServer - *-------------------------------------*
19:27:06.892 [main] INFO  c.a.jde.jdeconnectorserver.server.JDERestServer - *   Starting JDE Microservice 1.0.0   *
19:27:07.061 [main] INFO  c.a.jde.jdeconnectorserver.server.JDERestServer - *   JDE Microservice started!         *
19:27:07.064 [main] INFO  c.a.jde.jdeconnectorserver.server.JDERestServer - *-------------------------------------*
</pre>
<p>&nbsp;<br></p>

docker logs jd-atina-microserver

<pre class="center-column"> 
....
19:27:06.713 [main] INFO  c.acqua.jde.jdeconnectorserver.JDEConnectorServer - Iniciando JDE Service Impl...
19:27:06.891 [main] INFO  c.a.jde.jdeconnectorserver.server.JDERestServer - *-------------------------------------*
19:27:06.892 [main] INFO  c.a.jde.jdeconnectorserver.server.JDERestServer - *   Starting JDE Microservice 1.0.0   *
19:27:07.061 [main] INFO  c.a.jde.jdeconnectorserver.server.JDERestServer - *   JDE Microservice started!         *
19:27:07.064 [main] INFO  c.a.jde.jdeconnectorserver.server.JDERestServer - *-------------------------------------*
</pre>
<p>&nbsp;<br></p>

**Check JD Rest API Microservice startup**

<pre class="center-column"> 
docker logs jd-atina-rest-server
</pre>
<p>&nbsp;<br></p>

Output:

<pre class="center-column"> 
exec java -Dquarkus.http.host=0.0.0.0 -Djava.util.logging.manager=org.jboss.logmanager.LogManager -XX:+ExitOnOutOfMemoryError -cp . -jar /deployments/quarkus-run.jar
           ,ggg,
          dP""8I    I8
         dP   88    I8
        dP    88 88888888 gg
       ,8'    88    I8    ""
       d88888888    I8    gg    ,ggg,,ggg,     ,gggg,gg
 __   ,8"     88    I8    88   ,8" "8P" "8,   dP"  "Y8I
dP"  ,8P      Y8   ,I8,   88   I8   8I   8I  i8'    ,8I
Yb,_,dP       `8b,,d88b,_,88,_,dP   8I   Yb,,d8,   ,d8b,
 "Y8P"         `Y88P""Y88P""Y88P'   8I   `Y8P"Y8888P"`Y8
                          Powered by Quarkus 2.5.0.Final
19:32:14 INFO  [io.quarkus] (main) jd-atina-rest-server 1.0.0 on JVM (powered by Quarkus 2.5.0.Final) started in 8.869s. Listening on: http://0.0.0.0:8081 and https://0.0.0.0:8082
19:32:14 INFO  [io.quarkus] (main) Profile prod activated.
19:32:14 INFO  [io.quarkus] (main) Installed features: [cdi, logging-gelf, qute, resteasy, resteasy-jackson, resteasy-qute, scheduler, smallrye-context-propagation, smallrye-openapi, swagger-ui, vertx]
</pre>
<p>&nbsp;<br></p>

**Go to API defintions:**

[https://localhost/swagger/](https://localhost/swagger/)

