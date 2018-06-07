# setting_startup
Linuxでアプリを自動起動するための設定

start.sh
```sh
#!/bin/bash

source ~/.bashrc

cd `dirname $0`
unicorn -c unicorn.conf
```

myapi.service
```sh
[Unit]
Description = myapi

[Service]
ExecStart=/home/fancl01/myapi/start.sh
Restart=always
Type=simple
User=fancl01

[Install]
WantedBy=multi-user.target
```
