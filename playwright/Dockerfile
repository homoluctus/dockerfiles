FROM node:12-alpine3.12

RUN echo "http://dl-cdn.alpinelinux.org/alpine/edge/main" > /etc/apk/repositories \
    && echo "http://dl-cdn.alpinelinux.org/alpine/edge/community" >> /etc/apk/repositories \
    && echo "http://dl-cdn.alpinelinux.org/alpine/edge/testing" >> /etc/apk/repositories \
    && echo "http://dl-cdn.alpinelinux.org/alpine/v3.11/main" >> /etc/apk/repositories \
    && apk upgrade -U -a \
    && apk add --no-cache \
        libstdc++ \
        chromium \
        harfbuzz \
        nss \
        freetype \
        ttf-freefont \
        wqy-zenhei \
        ffmpeg \
    && rm -rf /var/cache/apk/*

# Add Chrome as a user
RUN mkdir -p /app \
    && adduser -D chrome \
    && chown -R chrome:chrome /app

# Run Chrome as non-privileged
USER chrome
WORKDIR /app

COPY --chown=chrome:chrome package.json yarn.lock ./
RUN yarn install -D

COPY --chown=chrome:chrome src .

CMD ["node", "index.js"]
