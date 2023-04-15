# Enable HTTPS with Spring Boot

Generate the server certificate, using RSA algorithm, store using PKCS12, validity 10 years, set password and certificate details interactively: 

`$> keytool -genkey -alias tomcat -storetype PKCS12 -keyalg RSA -keysize 2048 -keystore keystore.p12 -validity 3650`

For instance, set details for certificate as:

-   CN=ThesisMarket, OU=EntSoftArch-EPS, O=UdL, L=Lleida, ST=Lleida, C=ES

Validate the generated keystore by accessing its contents using:

`$> keytool -list -v -keystore keystore.p12 -storetype pkcs12`

Finally, configure Spring Boot to use the certificate and use HTTPS by adding to the "application.properties" configuration file the following properties:

-   server.port = 443
-   server.ssl.key-store = keystore.p12
-   server.ssl.key-store-password = mypassword
-   server.ssl.keyStoreType = PKCS12
-   server.ssl.keyAlias = tomcat