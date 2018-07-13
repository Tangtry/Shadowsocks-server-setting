# Shadowsocks-server-setting
how to set a shadowsocks on server

# Ubuntu as a example

##first install shadowsocks
> apt-get install shadowsocks

##edit the config file
> vim /etc/shadowsocks.json 

the config is something like 
```
{
"server":"0.0.0.0",
"server_port": 1234,
"local_address": "your_server_ipv4_address",
"local_port":1080,
"password": "password",
"timeout":300,
"method":"camellia-256-cfb",
"fast_open":"true"
}
```
## give the proper right for the file
>sudo chmod 755 /etc/shadowsocks.json

## run it
>sudo ssserver -c /etc/shadowsocks.json -d start


## ipv6 setting
Use the service from [Hurrican](https://tunnelbroker.net/)
![config pic](D:/Pictures/screenshot.png)

>ifconfig sit0 up
>ifconfig sit0 inet6 tunnel ::tunnel_ipv4_address
>ifconfig sit1 up
>ifconfig sit1 inet6 add ipv6_address::2/64
>route -A inet6 add ::/0 dev sit1
