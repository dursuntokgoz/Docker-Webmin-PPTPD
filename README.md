# Docker-Webmin
dockerfile for webmin （Webmin 的 Docker 镜像编译文件）

Download Webmin file:<br>
　　[https://prdownloads.sourceforge.net/webadmin/webmin_1.994_all.deb](https://prdownloads.sourceforge.net/webadmin/webmin_1.994_all.deb)<br>
Web Page Url:<br>
　　[https://www.webmin.com/download.html](https://www.webmin.com/download.html)<br>

## Building the image
```
git clone https://github.com/dursuntokgoz/Docker-Webmin-PPTPD.git
cd Docker-Webmin
docker build -t webmin/vpn .
```

## Export the image
```
docker save fribox/webmin -o docker.vpn-Webmin.tar
```

## Import the image 
```
docker load -i docker.vpn-Webmin.tar
```

## Running the container 
```
docker run --name PPTPd-Service -d --privileged --net=host --restart=always --env ROOT_PASSWORD="PassWord" --publish 10000:10000/tcp  --publish 1723:1723/tcp  --publish 1723:1723/udp webmin/vpn
```

## Log into webmin and manage your server
```
https://hostname.or.ip:10000
(root:pass)
```
Root Password Change : /usr/share/webmin/changepass.pl /etc/webmin admin pass
