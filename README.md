# logi-M585-M590-Multi-Device-Mouse

git here:
https://github.com/PixlOne/logiops

Default location for the configuration file is /etc/logid.cfg, but another can be specified using the -c flag.


```sh
sudo /usr/local/bin/logid -v -c /etc/logid.cfg
[DEBUG] CID  | reprog? | fn key? | mouse key? | gesture support?
[DEBUG] 0x50 |         |         | YES        | 
[DEBUG] 0x51 |         |         | YES        | 
[Gener] 0x52 | YES     |         | YES        | YES
[BACK]  0x53 | YES     |         | YES        | YES
[FORWD] 0x56 | YES     |         | YES        | YES
[LEFT]  0x5b | YES     |         | YES        | YES
[RIGHT] 0x5d | YES     |         | YES        | YES
[DEBUG] 0xd7 | YES     |         |            | YES
```

```sh
cat /lib/systemd/system/logid.service
[Unit]
Description=Logitech Configuration Daemon
StartLimitIntervalSec=0
After=multi-user.target
Wants=multi-user.target

[Service]
Type=simple
ExecStart=/usr/local/bin/logid -v -c /etc/logid.cfg
User=root
ExecReload=/bin/kill -HUP $MAINPID
Restart=always
RestartSec=3

[Install]
WantedBy=graphical.target
```
