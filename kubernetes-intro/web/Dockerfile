from nginx:1.17-alpine

EXPOSE 8000

RUN addgroup -S local && adduser -u 1001 -S -G local user 
RUN chown user /var/cache/nginx/
RUN chown user /var/run/

USER user

COPY nginx.conf /etc/nginx/nginx.conf
