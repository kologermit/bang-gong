FROM swaggerapi/swagger-ui

ENV API_URL swagger/res.yml

RUN apk add python3 
COPY ./start.py /entrypoint/
COPY ./entrypoint.sh /docker-entrypoint.d/50-entrypoint.sh
RUN chmod +x /docker-entrypoint.d/50-entrypoint.sh & mkdir -p /usr/share/nginx/html/swagger/