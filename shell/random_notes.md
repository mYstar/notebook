# Shell (zsh) stuff

## systemd

neuer Standard in der Linux Welt  

```shell
/etc/init.d/<tool> start
/etc/init.d/<tool> stop
# ...
# -->
systemctl start <tool>
systemctl stop <tool>
systemctl restart <tool>
systemctl status <tool>
```

## dig

Ablösung von`nslookup`
Kurze Variante: `dig +short <web adress>`

## tracepath

traceroute im userspace.
Ermittelt Geschwindigkeit + MTU.

Noch schöner: `mtr` == mytraceroute.
Ist ein `ping` + `traceroute` und hat bessere Darstellung.

## ifconfig 

sind out --> kann alles mit dem tool: `iproute2` erreicht werden.

```shell
ifconfig  
# --> 
ip addr show
ip link show
```

```shell
ifconfig eth0 up
# -->
ip link set eth0 up
ip link set eth0 down
```

## ripgrep

schnellere Variante für `grep`.

## exa

schönere und buntere Ausgaben als `ls`.

## watch progress

um den Fortschritt von prozessen, wie `cp` und so zu sehen.
auch: `watch progress -wc firefox`

## tldr

a little script + python project for simplifying man-pages.

## network manager

`sudo service network-manager restart`
