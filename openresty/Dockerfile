FROM openresty/openresty:1.13.6.2-2-alpine-fat
RUN mkdir /var/log/nginx

RUN apk add --no-cache openssl-dev
RUN apk add --no-cache git
RUN apk add --no-cache gcc
RUN luarocks install lua-resty-jwt && \
    luarocks install lua-resty-http && \
    luarocks install lua-resty-session
# && luarocks install lua-resty-openidc

RUN wget https://raw.githubusercontent.com/zmartzone/lua-resty-openidc/master/lib/resty/openidc.lua -P /usr/local/openresty/lualib/resty

ENTRYPOINT ["/usr/local/openresty/nginx/sbin/nginx", "-g", "daemon off;"]