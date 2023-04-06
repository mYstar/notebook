- scripts in: */etc/systemd/system* named *name.service*
- example script:
```shell
[Unit]
Description=SeaTable
After=network.target

[Service]
ExecStart=/opt/seatable/seatable-autostart.sh start
ExecStop=/opt/seatable/seatable-autostart.sh stop
User=root
Type=forking
TimeoutSec=0
RemainAfterExit=yes
GuessMainPID=no

[Install]
WantedBy=multi-user.target
```

- usage:
    - old: `/etc/init.d/<tool> start|stop`
    - `systemctl start|stop|restart <servicename>`: manual starting|stopping
    - `systemctl status <servicename>`
    - `systemctl enable|disable <servicename>`: autostart
    - `systemctl is-enabled <servicename>`: check autostart status