## mengatasi reverse proxy ssl/https self signed certificate
### add this to /etc/nginx/nginx.conf
proxy_ssl_protocols TLSv1.2 TLSv1.3;

proxy_ssl_ciphers DEFAULT;
