# How to use this image
## Start BIRD
Startup configuration `bird.conf` is mounted in /etc/bird.

```
$ docker run -d -v /path/bird.conf:/etc/bird/bird.conf iscream/bird
```
