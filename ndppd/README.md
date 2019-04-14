# How to use this image
## Start a NDP Proxy server
You write ndppd configuration file into \`pwd\`/ndppd.conf.  
And then run this image with current directory mounted in /etc/ndppd

```
$ docker run -v `pwd`:/etc/ndppd -d --net=host --cap-drop=ALL --cap-add=NET_RAW --cap-add=NET_ADMIN iscream/ndppd
```

# Reference
- [DanielAdolfsson/ndppd: NDP Proxy Daemon](https://github.com/DanielAdolfsson/ndppd)