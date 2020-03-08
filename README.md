# quick-ssl-certificates
Quickly generate SSL certificates for your domains on your development environment.

Copy the crt folder to your apache folder. If using xampp copy to ./xampp/apache/

Double click the make-cert.bat file. A command prompt will open. 

Type the domain you want the certificate generated.

open the newly created folder with your domain name and double click the server.crt file.

Install the certificate to your Local Machine Trusted Certificate Store.

Add the configuration to you C:\xampp\apache\conf\extra\httpd-vhosts.conf file

Sample config:


<VirtualHost dev.magento.com:8000>
    DocumentRoot "C:/xampp/htdocs/dev.magento.com"
    ServerName dev.magento.com
    ErrorLog "logs/dev.magento.com-error.log"
    CustomLog "logs/dev.magento.com-access.log" common
    <Directory "C:/xampp/htdocs/dev.magento.com">
		AllowOverride All
		Require local
	</Directory>
</VirtualHost>

<VirtualHost dev.magento.com:443>
    DocumentRoot "C:/xampp/htdocs/dev.magento.com"
    ServerName dev.magento.com
    ServerAlias *.magento.com
    SSLEngine on
    SSLCertificateFile "crt/dev.magento.com/server.crt"
    SSLCertificateKeyFile "crt/dev.magento.com/server.key"
</VirtualHost>

Restart Apache.

Add dev.magento.com to your hosts file C:\Windows\System32\drivers\etc\hosts

127.0.0.1 dev.magento.com

Done. 

Open your browser using https://dev.magento.com



