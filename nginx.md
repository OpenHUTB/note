


nginx出现 “414 request-uri too large”
nginx.conf修改http {
client_header_buffer_size 1m;  
large_client_header_buffers 4 1m; 


编译好的安装包
https://pkgs.org/download/nginx