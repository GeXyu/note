## 先clone项目，原因是需要翻墙
https://github.com/acmesh-official/acme.sh.git
cd acme.sh
./acme.sh --install 


## 切换CA,原因是默认zeroSSL 需要邮箱，还未去了解
acme.sh --set-default-ca --server letsencrypt

## 通过阿里云的API，进行DNS的验证
export Ali_Secret="fWF5HhfnOv37t0XSI4a7dn6RxwgU12"
export Ali_Key="LTAI5tR5svjZHLk4W9xTFn3Z"
acme.sh --issue -d 'nightscout.xilingbm.com'  --dns dns_ali

## 进行安装
acme.sh --install-cert -d 'nightscout.xilingbm.com' \
--key-file       /etc/nginx/cert/nightscout.xilingbm.com.key \
--fullchain-file /etc/nginx/cert/nightscout.xilingbm.com.pem \
--reloadcmd     "service nginx force-reload" 

## 强制续签
acme.sh --renew -d 'nightscout.xilingbm.com' --force
