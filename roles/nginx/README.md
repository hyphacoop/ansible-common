`Servers:` List of NGINX/SSL to deploy

`  "<Domain Name>"` Name of domain names to deploy. This should be the primary DNS to be used. 

`ssl_provider`: Define only is SSL is required, specify how SSL is to be generated. Valid options are `letsencrypt`,`letsencrypt_stageing`,`selfsign`

`web_hostname`: to be deprecated in favour of key (`<Domain Name>`)

`locations`: List of locations for the site. You can specify many locations however  `/` is required


`web_additional`: Additional SSL domain names to add to certificate. Format: DNS:<domain2>,DNS:<domain3>
`  "<Location>"` absolute URL path

`local_location`: Path to local folder

`proxy_location`: Reverse Proxy url


`cors`: set to true to add allow cors headers in NGINX
  
Example:
```
all:
  children:
    server:
      hosts:
        127.0.0.1:
          servers:
            "First.Domain":
              ssl_provider: selfsign
              web_hostname: First.Domain
              locations:
                "/":
                  local_location: /var/www/html
                  cors: true
                "/path2":
                  proxy_location: http://127.0.0.1:8080
            "Second.Domain":
              ssl_provider: letsencrypt
              web_hostname: Second.Domain
              web_additional: DNS:www.Second.Domain,DNS:ftp.Second.Domain
              locations:
                "/":
                  local_location: /var/www/html
                "/path2":
                  proxy_location: http://127.0.0.1:8080
                  cors: true
```
