
/etc/nginx/comf.d/my.conf

```
server {
        listen 80;
        server_name devops.aradarpanet.com;
        return 301 https://devops.aradarpanet.com$request_uri;
}
server {
        listen 443 ssl;
        server_name devops.aradarpanet.com;
        ssl_certificate ssl/public.crt;
        ssl_certificate_key ssl/private.key;
        location / {

                proxy_pass http://192.168.64.1:8080/app/ ;
        }
}
```
