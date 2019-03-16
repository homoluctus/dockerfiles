# How to use thie image
## Start a dnscrypt-proxy server

```
$ docker run -d iscream/dnscrypt-proxy
```

## Expose external port

```
$ docker run -d -p 53:53 iscream/dnscrypt-proxy
```

## Use a custom configuration
This image executes dnscrypt-proxy -config /etc/dnscrypt-proxy/dnscrypt-proxy.toml in default.
You write the configuration file dnscrypt-proxy.toml into $PWD/conf directory  
and mount it to /etc/dnscrypt-proxy directory in the container.

```
$ docker run -d -v $PWD/conf:/etc/dnscrypt-proxy iscream/dnscrypt-proxy
```
