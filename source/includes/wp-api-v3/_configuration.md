# Configuration #

## Requirements ##

### Requirements to consume Web Services using JD Atina WS Microservices ###

To use the latest version of the JD Atina REST WS API you will need:

* JD Atina Web Services Microservices 1.0.0+ running.
* Oracle JD Edwards EnterpriseOne HTML Client credential: User, Pasword, Environment and Role.
* You may access the API over either HTTP or HTTPS, but *HTTPS is recommended where possible*.


### Requirements to install JD Atina WS Microservices ###

* Oracle JD Edwards EnterpriseOne Server Manager credential: jde admin user, Pasword and url for Server Manager Ex. http://server:8999/manage/

* [Docker](https://docs.docker.com/get-docker/ "Docker"). JD Atina Web Service Microserver run under Docker container.

* Following folder inside JDE Deployment Server:

    * `//Deplo/E920/MISC`
    * `//Deplo/E920/system/Classes`
    * `//Deplo/E920/system/JAS/webclient.ear/webclient.war/WEB-INF/lib`
    * `//Deplo/E920/DV920/java/sbfjars`


### Addionals Requirements to use JD Generate Configuration Files and JD Generate Jars Files Tools ###

* JDK 8 installed with JAVA_HOME configured appropriately (It not requires for docker version)

* Apache Maven 3.8.1+

![JD Atina Configuration Tool](images/note-icon.png) Verify Maven is using the Java you expect
If you have multiple JDK’s installed it is not certain Maven will pick up the expected java and you could end up with unexpected results. 
You can verify which JDK Maven uses by running mvn --version.
  
  
## JD Atina Additional Tools ##

Use the following tools to start the configuration process.

* JD Atina Generate Configuration Files Tool
* JD Atina Generate Jars Files Tool
 
## JD Atina Generate Configuration Files Tool ##
  
JD WS Microservice needs the following ini files according to your environment:

* jdbj.ini
* jdeinterop.ini
* jdelog.properties
* tnsnames.ora" (for Oracle RDBMS based installations only)

![JD Atina Configuration Tool](images/atina_ini_config_tool.png)

You can configure it manually following JDE manuals or you can use this tools to help you.

This tool help to you to generate a base ini files.

It takes all information from JDE Enterprise Server Manager using REST API for Server Manager

The tooll will require to select the HTML Client instance according to your environment.

![JD Atina Configuration Tool](images/note-icon.png) At the end of this process, We recommend review jdeinterop.ini and jdbj.ini files before deploy it on JD Atina
Web Service Microservice using this guide: [Understanding jdeinterop.ini File](https://docs.oracle.com/cd/E24705_01/doc.91/e24221/jdeinterop_java.htm#EOTCN00333)
	 
	 
### JD Atina Generate Configuration Files Tool - Using JAVA APP ###

It will require openjdk 8 installed.

Download [JD Atina Generate Configuration Files Tool](http://157.245.236.175:8081/artifactory/libs-release-local/com/atina/jd-create-ini-files/1.0.0/jd-create-ini-files-1.0.0-jar-with-dependencies.jar) - latest release:


<pre class="center-column">
curl http://157.245.236.175:8081/artifactory/libs-release-local/com/atina/jd-create-ini-files/1.0.0/jd-create-ini-files-1.0.0-jar-with-dependencies.jar \
--output jd-create-ini-files-1.0.0-jar-with-dependencies.jar
</pre>
<p>&nbsp;<br></p>
 
Run jd-create-ini-files command:

<pre class="center-column">
  java -jar jd-create-ini-files-1.0.0-jar-with-dependencies.jar [OPTIONS]

  OPTIONS:                                                                       
Options category 'startup':
  --debug [-d] (a string; default: "N")
    Debug Option
  --environment [-e] (a string; default: "")
    JDE Environment
  --password [-p] (a string; default: "")
    JDE Password for Enterprise Server Manager
  --server [-s] (a string; default: "")
    JDE URL of Server Manager
  --user [-u] (a string; default: "")
    JDE User for Enterprise Server Manager
</pre>
<p>&nbsp;<br></p>
 
Usage Exampes

<pre class="center-column">
java -jar jd-create-ini-files-1.0.0-jar-with-dependencies.jar \
-u jde_admin \
-p XXXXXXX \
-s http://server-manager:8999/manage \
-e JDV920
</pre>
<p><br>&nbsp;<br></p>

 
### JD Atina Generate Configuration Files Tool - Using Docker instead of Java Application ###
 
Usage Example:

<pre class="center-column">
docker run --rm -v /tmp/build_jde_libs:/tmp/build_jde_libs/ -i \
--name jd-create-ini-files 92455890/jd-create-ini-files:1.0.0 \
jde_admin jde_password JPS920 http://servermanager.com:8999/manage
</pre>
<p>&nbsp;<br></p>

### Reviewing Output ###

<pre class="center-column">
Folder : /tmp/build_jde_libs/JPS920 has been created

Authenticating : http://server-manager:8999/manage
         Cookie: 044GXl43PnHkTe1L3AMc/siNkFOIoll+S4ngsdGnNkS7Qg=MDA5MDE1MDE1amRlX2FkbWluMTM0LjIwOS4yMTEuMjQ4MTM0LjIwOS4yMTEuMjQ4MTYzNzYwNzAxMTIzOQ==
Getting Server Groups : http://server-manager:8999/manage

Select HTML Instance for environment JPS920:
0 - alpha_db
1 - alpha_dep
2 - alpha_dv920
3 - alpha_ent
4 - html_ps920
Q - Quit
4
Option Selected: 4

JDE Instance selected: html_ps920

Getting Instance Values: http://server-manager:8999/manage for Instance Name 'html_ps920'
 Processing File: jdbj.ini
 Processing File: jdeinterop.ini
 Processing File: jdelog.properties
 Processing File: settings.xml

------------------------------------------------------------------------
GENERATION SUCESSS
------------------------------------------------------------------------
 File: \tmp\build_jde_libs\JPS920\jdbj.ini generated
 File: \tmp\build_jde_libs\JPS920\jdeinterop.ini generated
 File: \tmp\build_jde_libs\JPS920\jdelog.properties generated
 File: \tmp\build_jde_libs\settings.xml generated
------------------------------------------------------------------------
</pre>
<p>&nbsp;<br></p>

It will create the following files:

<pre class="center-column"> 
build_jde_libs
      ├─ settings.xml
      ├─ JPS920
      ├─────├─ jdbj.ini
      ├─────├─ jdeinterop.ini
      └─────└─ jdelog.properties            
</pre>
<p>&nbsp;<br></p>


Adding manually "tnsnames.ora" for Oracle RDBMS based installations only.

Edit jdeinterop.ini to set correct server IP's:

<pre class="center-column"> 
[DNS_SERVERS]
JDE-ENT=2.2.2.2
JDE-SQL=1.1.1.1           
</pre>
<p>&nbsp;<br></p>


## JD Atina Generate Jars Files Tool ##

This tool will generate all jars files need it by JD Web Service Microservice.

![JD Atina Generate Jars Files](images/atina_jar_tool.png)
 

**Preparing folders**

Create folder with the following structure under **/tmp/build_jde_libs**:

<pre class="center-column"> 
tmp
└─build_jde_libs
      ├─ JDBC_Vendor_Drivers
      └─ system
         │─ Classes 
         │─ JAS    
         └─ WS            
</pre>
<p>&nbsp;<br></p>

**Copy files from JDE Deploment Server to the corresponding folders**

| Destination              | Source                                                                       |
| ------------------------ | ---------------------------------------------------------------------------- |
|/tmp  |                   |                                                                              |
|/tmp/build_jde_libs       |                                                                              |
|   ->/JDBC_Vendor_Drivers | //Deployment Server/E920/MISC/*                                              |
|   ->/system/Classes      | //Deployment Server/E920/system/Classes\*                                    |
|   ->/system/JAS          | //Deployment Server/E920/system/JAS/webclient.ear/webclient.war/WEB-INF/lib/*|
|   ->/system/WS           | //Deployment Server/E920\DV920/java/sbfjars/*                                |

**Define local Repository (localRepo option)**

This option is required to run this tool using JAVA apps locally.

Running this command you can get where the curret local repository is defined:

<pre class="center-column"> 
mvn help:evaluate -Dexpression=settings.localRepository     
</pre>
<p>&nbsp;<br></p>

In this output we see /root/.m2/repository

<pre class="center-column"> 
[INFO]
[INFO] ------------------< org.apache.maven:standalone-pom >-------------------
[INFO] Building Maven Stub Project (No POM) 1
[INFO] --------------------------------[ pom ]---------------------------------
[INFO]
[INFO] --- maven-help-plugin:3.2.0:evaluate (default-cli) @ standalone-pom ---
[INFO] No artifact parameter specified, using 'org.apache.maven:standalone-pom:pom:1' as project.
[INFO]
/root/.m2/repository  <==  ****** THIS IS THE VALUE REQUIRED *******
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  3.301 s
[INFO] Finished at: 2021-11-22T20:31:42Z
[INFO] ------------------------------------------------------------------------     
</pre>
<p>&nbsp;<br></p>


### JD Atina Generate Jars Files Tool - Using Java Application ###

It will require openjdk 8 installed.

Download [JD Atina Generate Jars Files Tool](http://157.245.236.175:8081/artifactory/libs-release-local/com/atina/jd-create-jar-files/1.0.0/jd-create-jar-files-1.0.0-jar-with-dependencies.jar) - latest release:

<pre class="center-column"> 
curl http://157.245.236.175:8081/artifactory/libs-release-local/com/atina/jd-create-jar-files/1.0.0/jd-create-jar-files-1.0.0-jar-with-dependencies.jar \
--output jd-create-jar-files-1.0.0-jar-with-dependencies.jar     
</pre>
<p>&nbsp;<br></p>

Run jd-create-ini-files command:

<pre class="center-column">
Usage: java -jar jd-create-jar-files-1.0.0-jar-with-dependencies.jar OPTIONS

Options category 'startup':
  --accion [-a] (a string; default: "3")
    Accion: 1: Generate JDE Bundle 2: Build WS 3: Both
  --clean [-c] (a string; default: "Y")
    clean
  --jdbcDriver [-j] (a string; default: "/tmp/build_jde_libs/JDBC_Vendor_Drivers")
    Enter JDBC Driver Folder
  --jdeInstallPath [-i] (a string; default: "/tmp/build_jde_libs/")
    Enter JDE Path installed
  --localRepo [-r] (a string; default: "")
    Enter Maven Local Repo
  --settings [-s] (a string; default: "/tmp/build_jde_libs/settings.xml")
    settings.xml to use Ex. /apache-maven-3.8.1/conf/settings.xml
  --version [-o] (a string; default: "1.0.0")
    Enter Version
</pre>
<p>&nbsp;<br></p>
 
Usage Exampes

<pre class="center-column">
java -jar jd-create-jar-files-1.0.0-jar-with-dependencies.jar -r /root/.m2/repository
</pre>
<p>&nbsp;<br></p>


### JD Atina Generate Jars Files Tool - Using Docker instead of Java Application ###

Run the following docker command:

<pre class="center-column">
docker run --rm -v /tmp/build_jde_libs:/tmp/build_jde_libs/ \
	-i --name jd-create-jar-files 92455890/jd-create-jar-files:1.0.0
</pre>
<p>&nbsp;<br></p>


### Reviewing Output ###


<pre class="center-column">
------------------------------------------------------------------------
GENERATION SUCESSS
------------------------------------------------------------------------
JDE Library bundle has been copied to: /tmp/build_jde_libs/jde-lib-wrapped-1.0.0.jar
JDE WS has been copied to: /tmp/build_jde_libs/StdWebService-1.0.0.jar
------------------------------------------------------------------------
</pre>
<p>&nbsp;<br></p>

It will create the following files:

<pre class="center-column">
build_jde_libs
      ├─ jde-lib-wrapped-1.0.0.jar
      └─ StdWebService-1.0.0.jar
</pre>
<p>&nbsp;<br></p>


## Deploy artifact to Local Repository - Optional ##

This optional. 
At startup, JD Microservice has the option to get these libraries from an internal repository.
 
In case you want to use a local repository, exectute the following command:

<pre class="center-column">
mvn deploy:deploy-file \
	-DgroupId=com.jdedwards \
	-DartifactId=jde-lib-wrapped \
	-Dversion=1.0.0 \
	-DrepositoryId=repo-central \
	-Dpackaging=jar \
	-Dfile=\tmp\build_jde_libs\jde-lib-wrapped-1.0.0.jar \
	-Durl=http://localrepo:8081/artifactory/libs-release
</pre>
<p>&nbsp;<br></p>

<pre class="center-column">
mvn deploy:deploy-file \
	-DgroupId=com.jdedwards \
	-DartifactId=StdWebService \
	-Dversion=1.0.0 \
	-DrepositoryId=repo-central \
	-Dpackaging=jar \
	-Dfile=\tmp\build_jde_libs\StdWebService-1.0.0.jar \
	-Durl=http://localrepo:8081/artifactory/libs-release
</pre>
<p>&nbsp;<br></p>
