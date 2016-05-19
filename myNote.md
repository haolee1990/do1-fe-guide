//让node以sudo权限运行
whereis node

/usr/local/bin/node

sudo setcap 'cap_net_bind_service=+ep' + [nodepath]
