# setting_startup
Linuxでアプリを自動起動するための設定

start.sh
```sh
#!/bin/sh
export PATH="$HOME/.anyenv/bin:$PATH"
eval "$(anyenv init -)"
cd `dirname $0`

node index.js
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
