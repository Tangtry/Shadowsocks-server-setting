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

If using ipv6, server should be 
> "server": "::",

## give the proper right for the file
>sudo chmod 755 /etc/shadowsocks.json

## install chacha20 support
```
apt-get install build-essential
wget https://download.libsodium.org/libsodium/releases/LATEST.tar.gz
tar xf libsodium-1.0.10.tar.gz && cd libsodium-stable
./configure && make -j4 && make install
ldconfig
```



## run it
>sudo ssserver -c /etc/shadowsocks.json -d start


## ipv6 setting
Use the service from [Hurrican](https://tunnelbroker.net/)
And find the settings from here
![config pic](https://github.com/Tangtry/Shadowsocks-server-setting/blob/master/screenshot.png)
```
ifconfig sit0 up
ifconfig sit0 inet6 tunnel ::tunnel_ipv4_address
ifconfig sit1 up
ifconfig sit1 inet6 add ipv6_address::2/64
route -A inet6 add ::/0 dev sit1
```
