# How to create a virtual host on Manjaro using Apache (httpd)

Set host name on hosts

```
sudo nano /etc/hosts
```
```
127.0.0.1  example.com
```

edit httpd vhost config file

```
sudo nano /etc/httpd/conf/extra/httpd-vhosts.conf
```

insert the configurations

```
<VirtualHost *:80>
    ServerName example.com
    ServerAlias www.example.com
    DocumentRoot /srv/http/example
    ErrorLog /srv/http/example/error.log
    CustomLog /srv/http/example/requests.log combined
</VirtualHost>
```
Plus if u want https (need to install local cert maker, can use mkcert) 

the command Listen 443 only for the first

```
Listen 443
<VirtualHost _default_:443>
        Protocols h2 h2c http/1.1
    ServerName neolive.com
    SSLEngine on
    SSLCertificateFile "/srv/ssl/example.com.pem"
    SSLCertificateKeyFile "/srv/ssl/example.com-key.pem"
    DocumentRoot /srv/http/example
    ErrorLog /srv/http/example/error.log
    CustomLog /srv/http/example/requests.log combined
    <Directory "/srv/http/example">
        AllowOverride All
    </Directory>
</VirtualHost>
```
After that just create a the directory in the path you put on virtual host

```
sudo mkdir /srv/http/example
```

### If you want to use Apache as SPA (single page app) add this to http.conf
```
sudo nano /etc/httpd/conf/httpd.conf
```
```
# Map all SPA-looking routes to our single page app index file
<Directory ~ "^/[\w+\d+-]+">
  FallbackResource /index.html
</Directory>

# Requests for files should return a real 404 and not fallback to the index.html page, though
<Files ~ "\.(js|css|gif|jpe?g|png)$">
  FallbackResource disabled
  ErrorDocument 404 "File not found"
</Files>
```
from [stackoverflow answer](https://stackoverflow.com/questions/54897317/apache-settings-for-spa-using-html5-history-routing)
