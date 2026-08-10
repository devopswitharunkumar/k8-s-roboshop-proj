FROM python:3.9-alpine
EXPOSE 8080
#keeping them in k8's secrets
# ENV AMQP_USER=roboshop \
#     AMQP_PASS=roboshop123   
USER root
WORKDIR /app
COPY requirements.txt /app/
RUN apk add --no-cache pcre-dev \
    && apk add --no-cache --virtual .build-deps build-base linux-headers python3-dev \
    && pip install --no-cache-dir -r requirements.txt \
    && apk del .build-deps
COPY *.py /app/
COPY payment.ini /app/

CMD [ "uwsgi", "--ini", "payment.ini"]
