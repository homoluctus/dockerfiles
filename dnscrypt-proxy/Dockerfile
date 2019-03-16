FROM alpine:3.9 as builder
WORKDIR /tmp
RUN apk add --no-cache ca-certificates curl tar \
    && curl -o dnscrypt-proxy.tar.gz -L https://github.com/jedisct1/dnscrypt-proxy/releases/download/2.0.21/dnscrypt-proxy-linux_x86_64-2.0.21.tar.gz \
    && tar -xzvf dnscrypt-proxy.tar.gz

FROM alpine:3.9
RUN apk add --no-cache ca-certificates \
    && mkdir /etc/dnscrypt-proxy /var/log/dnscrypt-proxy
COPY --from=builder /tmp/linux-x86_64/dnscrypt-proxy /usr/local/bin/
COPY --from=builder /tmp/linux-x86_64/example-dnscrypt-proxy.toml /etc/dnscrypt-proxy/dnscrypt-proxy.toml
RUN chmod 500 /usr/local/bin/dnscrypt-proxy \
    && chmod 644 /etc/dnscrypt-proxy/dnscrypt-proxy.toml \
    && sed -i 's/^# server_names/server_names/' /etc/dnscrypt-proxy/dnscrypt-proxy.toml \
    && echo 'nameserver 127.0.0.1\noptions edns0 single-request-reopen' > /etc/resolv.conf

EXPOSE 53/udp
EXPOSE 53/tcp
CMD ["/usr/local/bin/dnscrypt-proxy", "-config", "/etc/dnscrypt-proxy/dnscrypt-proxy.toml"]
