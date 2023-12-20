acme.sh --set-default-ca --server letsencrypt

export Ali_Secret="fWF5HhfnOv37t0XSI4a7dn6RxwgU12"
export Ali_Key="LTAI5tR5svjZHLk4W9xTFn3Z"
acme.sh --issue -d 'nightscout.xilingbm.com'  --dns dns_ali

acme.sh --install-cert -d 'nightscout.xilingbm.com' \
--key-file       /etc/nginx/cert/nightscout.xilingbm.com.key \
--fullchain-file /etc/nginx/cert/nightscout.xilingbm.com.pem \
--reloadcmd     "service nginx force-reload" 

acme.sh --renew -d 'nightscout.xilingbm.com' --force
