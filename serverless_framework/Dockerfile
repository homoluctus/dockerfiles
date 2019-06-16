FROM node:8-alpine
RUN mkdir /root/app
WORKDIR /root/app
RUN npm i serverless -g --no-cache
RUN apk add --no-cache \
    python3
RUN pip3 install --upgrade --no-cache-dir \
    pip \
    awscli