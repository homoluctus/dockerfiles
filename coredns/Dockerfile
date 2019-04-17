FROM debian:stretch-slim as builder
ENV COREDNS_VERSION 1.5.0
RUN apt update && \
    apt install -y --no-install-recommends \
        ca-certificates \
        curl && \
    curl -LO https://github.com/coredns/coredns/releases/download/v${COREDNS_VERSION}/coredns_${COREDNS_VERSION}_linux_amd64.tgz && \
    tar xzvf coredns_${COREDNS_VERSION}_linux_amd64.tgz -C /usr/local/bin

FROM debian:stretch-slim
COPY --from=builder /usr/local/bin/coredns /usr/local/bin/
RUN mkdir /etc/coredns && \
    if [ ! -d "/etc/ssl/certs" ]; then \
        mkdir -p /etc/ssl/certs; \
    fi
COPY --from=builder /etc/ssl/certs/ca-certificates.crt /etc/ssl/certs/
EXPOSE 53/udp 53/tcp
CMD ["coredns", "-conf", "/etc/coredns/Corefile"]
