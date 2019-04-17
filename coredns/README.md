# How to use this image
## Start a CoreDNS server
You write CoreDNS startup configuration file into \`pwd\`/conf/Corefile.
And then run this image with \`pwd\`/conf directory mounted in /etc/coredns

```
$ docker run -v `pwd`/conf:/etc/coredns -p 53:53 -d iscream/coredns
```

