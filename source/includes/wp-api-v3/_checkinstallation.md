# JDE Check JD Microservice executing a Web Service #

This tool is used to test JD Microservice. 
It will invoke a simple WS.

Download [JD Atina Check Web Service Microservice](http://157.245.236.175:8081/artifactory/libs-release-local/com/atina/jd-check-microservice/1.0.0/jd-check-microservice-1.0.0-jar-with-dependencies.jar) - latest release:

Run jd-create-ini-files command:

<pre class="center-column">
Usage: java -jar jd-check-microservice OPTIONS

   Options category 'startup':

  --mode [-m] (a string; default: "TestLoggindAndGetAddressBookWS")
    Modes
  --user [-u] (a string; default: "")
    JDE User
  --password [-w] (a string; default: "")
    JDE Password
  --environment [-e] (a string; default: "")
    JDE Environment
  --role [-r] (a string; default: "")
    JDE Role
  --serverName [-s] (a string; default: "")JD Micreserver Name or IP
  --serverPort [-p] (a string; default: "")
    JD Micreserver Port
  --addressbookno [-a] (a string; default: "")
    Address Book No
</pre>
<p>&nbsp;<br></p>

Usage Exampes

<pre class="center-column">
java -jar jd-check-microservice-1.0.0-jar-with-dependencies.jar -u JDE -w XXXXXX -e JDV920 -r *ALL -s localhost -p 8077 -m TestLoggindAndGetAddressBookWS -a 28
</pre>
<p>&nbsp;<br></p>

Output 

<pre class="center-column">
Checking Microservice...
user=JDE, environment=JDV920, role=*ALL, serverName=192.168.99.100, serverPort=8077, mode=TestLoggindAndGetAddressBookWS, addressbookno=1, sessionId=, transactionId=
Transaction ID: 20211122124518
User User: JDE in environment JDV920 with *ALL connected with Session ID [-1636010069]
WS JP010000.AddressBookManager.getAddressBook has been called correctly
Logout [0]
------------------------------------------------------------------------
CHECK SUCESSS
------------------------------------------------------------------------
User User: JDE in environment JDV920 with *ALL connected with Session ID -1636010069
Address Book Name: Financial/Distribution Company --
User User: JDE in environment JDV920 with *ALL disconnected. Current session ID 0
------------------------------------------------------------------------
</pre>
<p>&nbsp;<br></p>

