---
title: Disable sslv3 and sslv2 POODLE SSLv3 Vulnerability Tomcat
id: disable-sslv3-sslv2
---

# Solution

By default, the Tomcat SSL connector is configured to use the TLSv1,TLSv1.1,TLSv1.2, so no action is normally required.

1. Make sure Tomcat is updated and deployed

  ![SSL Protocols](../../assets/local/images/ssl-protocols.png)

2. You could additionally log into the server and you should see the following in server.xml

    ```xml
 sslEnabledProtocols
     <Connector port="8443"

     protocol="HTTP/1.1" SSLEnabled="true"

     maxThreads="50"

     keystoreFile="/app/certs/keystore.jks"

     keystorePass="changeit"

     scheme="https" secure="true"

     clientAuth="false"  sslProtocol="TLSv1" sslEnabledProtocols="TLSv1,TLSv1.1,TLSv1.2"
      />
   ```

# See Also

* [https://access.redhat.com/solutions/1232233](https://access.redhat.com/solutions/1232233)
* [https://wiki.apache.org/tomcat/Security/POODLE](https://wiki.apache.org/tomcat/Security/POODLE)
* [https://wiki.apache.org/tomcat/Security/POODLE](https://wiki.apache.org/tomcat/Security/POODLE) - Look for Poodle detector attachment
* [https://access.redhat.com/articles/1232123](https://access.redhat.com/articles/1232123)
