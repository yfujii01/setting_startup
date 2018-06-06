# setting_startup
Linuxでアプリを自動起動するための設定

```sh
echo start

if [ $# -ne 2]; then
  echo "引数が足りません" 1>&2
  echo "引数1:アプリ名" 1>&2
  echo "引数2:起動スクリプト" 1>2
  exit 1
fi

# アプリ名.serviceを作成
sudo cat << EOS > /etc/systemd/system/${1}.service
[Unit]
Description = ${1}

[Service]
ExecStart=${2}
Restart=always
Type=simple
User=`whoami`

[Install]
WantedBy=multi-user.target
EOS

echo end
```
