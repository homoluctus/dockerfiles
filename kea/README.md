# How to use this image
## Start a Kea DHCP server
You write Kea startup configuration file into \`pwd\`/conf/keactrl.conf and kea-dhcpv4.conf etc.  
And then run this image with \`pwd\`/conf mounted in /etc/kea.

```
$ docker run --net=host --cap-add=NET_BIND_SERVICE --cap-add=NET_BROADCAST --cap-drop=ALL -v `pwd`/conf:/etc/kea -d iscream/kea:latest
```

