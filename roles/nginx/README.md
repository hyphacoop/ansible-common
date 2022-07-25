# nginx

Install nginx and set up websites with reverse-proxies.

*NOTE* Remember to open port 80 and or 443 on firewall for remote use.
80 required for LetsEncrypt as well.

## `nginx_sites:` 

- Dictionary of websites to deploy. 
- Dict key is the cosmetic name of each site

Attributes:

- `ssl_provider`: Define only is SSL is required, specify how SSL is to be generated.  Valid options are `letsencrypt`,`letsencrypt_stageing`,`selfsign`
- `web_hostname`: Domain name to use for vhost/ssl certificate
- `web_additional`: Additional SSL domain names to add to certificate. Format: DNS:<domain2>,DNS:<domain3>
- `locations`: 

  Dictionary of locations for the site. You can specify 
  many locations, however `/` is required

  Dict key is the absolute URL path

    - `local_location`: Path to local folder
    - `proxy_location`: Reverse-proxy URL. Defining enables reverse-proxying
    - `cors`: Set to true to add add CORS headers in nginx
    - `proxy_websocket`: Set to true to enable websocket support for reverse-proxy
    - `basic_auth_file`: If defined enables basic http authentication using specified files
    - `basic_auth_description`:  (default "Login") Defines text to appear in authentication box

  
Example:
```yaml
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
