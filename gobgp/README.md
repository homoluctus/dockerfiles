# How to use this image
## Start a GoBGP server

```
$ docker run -d iscream/gobgp gobgpd
```

## Exposing externanl port

```
$ docker run -d -p 179:179 iscream/gobgp gobgpd
```

## Using a custom GoBGP
You write GoBGP startup configuration file into \`pwd\`/gobgp.conf.  
And then run this image with current directory mounted in /etc/gobgp

```
$ docker run -v `pwd`:/etc/gobgp -d iscream/gobgp
```

