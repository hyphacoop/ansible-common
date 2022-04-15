# Define NGINX Config

*NOTE* Remember to open port 80 and or 443 on firewall for remote use. 80 required for LetsEncrypt as well

## `nginx_sites: ` 

- DICT of NGINX/SSL to deploy. 
- DICT `KEY` is the cosmetic name of each site

Attributes:

- `ssl_provider`: 

  Define only is SSL is required, specify how SSL is to be generated.  Valid options are `letsencrypt`,`letsencrypt_stageing`,`selfsign`

- `web_hostname`: 

  Domain name to use for vhost/ssl certificate

- `web_additional`: Additional SSL domain names to add to certificate. Format: DNS:<domain2>,DNS:<domain3>


- `locations`: 

  DICT of locations for the site. You can specify 
  many locations however `/` is required

  DICT `KEY` is the absolute URL path

    - `local_location`: Path to local folder

    - `proxy_location`: Reverse Proxy URL. Defining enables reverse proxy code

    - `cors`: Set to true to add ALLOW cors headers in NGINX
    - `proxy_websocket`: Set to true to enable websocket support for reverse proxy

    - `basic_auth_file`: If defined enables basic http authentication using specified files

    - `basic_auth_description`:  (default "Login") Defines text to appear in authentication box

  
Example:
```
all:
  children:
    server:
      hosts:
        127.0.0.1:
          nginx_sites:
            "First.Domain":
              ssl_provider: selfsign
              web_hostname: First.Domain
              locations:
                "/":
                  local_location: /var/www/html
                  cors: true
                "/path2":
                  proxy_location: http://127.0.0.1:8080
                  proxy_websocket: true
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
