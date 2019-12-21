# netflix sniproxy

this code testing on ubuntu 18.04.* is ok.

```
apt-get install sniproxy dnsmasq -y
cp dnsmasq.conf /etc/dnsmasq.conf
cp sniproxy.conf /etc/sniproxy.conf

curl -s http://nginx.org/keys/nginx_signing.key | apt-key add -
cat > /etc/apt/sources.list.d/nginx.list << EOF
deb http://nginx.org/packages/$(. /etc/os-release; echo "$ID")/ $(lsb_release -cs) nginx
deb-src http://nginx.org/packages/$(. /etc/os-release; echo "$ID")/ $(lsb_release -cs) nginx
EOF
apt-get update
apt-get install nginx -y
# change nginx configure file `92` line for your server ip
cp nginx.conf /etc/nginx/nginx.conf

systemctl restart sniproxy dnsmasq nginx
systemctl enable sniproxy dnsmasq nginx
```

# v2ray setting

please read the `v2ray.json` file.

modify the `121` line with your sniproxy server ip address

then run this command:

```
sed  "1i\nameserver sniproxyip" /etc/resolv.conf
```

enjoy it.


debian  的测试源

添加源，编辑sources.list文件，vi /etc/apt/sources.list，添加以下内容

```
deb http://httpredir.debian.org/debian buster main
```

安装sniproxy，首先要检查更新，然后再安装

```
apt update
apt install sniproxy
```
