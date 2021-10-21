Baseado em: https://github.com/selivan/https-ssl-cert-check-zabbix


```bash
cd /usr/lib/zabbix/externalscripts
wget https://raw.githubusercontent.com/remontti/https-ssl-cert-check-zabbix/master/ssl_cert_check.sh
wget https://raw.githubusercontent.com/remontti/https-ssl-cert-check-zabbix/master/ssl_cert_list
```
Edite o ssl_cert_list e informe os domínios/porta a ser monitorado.
```bash
chmod +x ssl_cert_check.sh
cd /etc/zabbix/zabbix_agentd.d
wget https://raw.githubusercontent.com/remontti/https-ssl-cert-check-zabbix/master/userparameters_ssl_cert_check.conf
mkdir /var/lib/zabbix
chown zabbix:zabbix /var/lib/zabbix
chown zabbix. /usr/lib/zabbix/externalscripts/ -R
systemctl restart zabbix-agent
```

Importe o template e Host para de zabbix 5.x

Uso no terminal/faça teste:
```bash
cd /usr/lib/zabbix/externalscripts
./ssl_cert_check.sh valid meudominio.com.br
./ssl_cert_check.sh valid meudominio.com.br 443
./ssl_cert_check.sh valid meudominio.com.br 8080
./ssl_cert_check.sh valid 192.168.0.1 meudominio.com.br 443 30
./ssl_cert_check.sh valid mail.meudominio.com.br 25/smtp
1 Válido
0 Inválido

./ssl_cert_check.sh expire meudominio.com.br
52 - Dias para expirar
```
