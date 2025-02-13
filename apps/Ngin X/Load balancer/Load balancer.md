

/etc/nginx/comf.d/my.conf


```

proxy_cache_path /data/nginx/cache keys_zone=mycache:10m;
upstream backend {

        server 192.168.64.1:8080;
        server 192.168.64.2:8080;
}

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
                proxy_cache mycache;
                proxy_pass http://backend/app/ ;
        }
}


https://docs.nginx.com/nginx/admin-guide/content-cache/content-caching/

https://docs.nginx.com/nginx/admin-guide/load-balancer/http-load-balancer/
https://nginx.com/blog/nginx-caching-guide


        location ~* \.(?:manifest|jpeg|api)$ {
                expires -1;
        }

        location ~* \.(?:css|jpeg)$ {
                expires 1h;
        }

```
