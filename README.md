# Docker-Webmin
dockerfile for webmin 

Download Webmin file:<br>
　　[https://prdownloads.sourceforge.net/webadmin/webmin_1.994_all.deb](https://prdownloads.sourceforge.net/webadmin/webmin_1.994_all.deb)<br>
Web Page Url:<br>
　　[https://www.webmin.com/download.html](https://www.webmin.com/download.html)<br>

## Building the image
```
sudo git clone https://github.com/dursuntokgoz/Docker-Webmin-PPTPD.git
cd Docker-Webmin-PPTPD
sudo docker build -t webmin/vpn .
```

## Export the image
```
sudo docker save webmin/vpn -o docker.vpn-Webmin.tar
```

## Import the image 
```
sudo docker load -i docker.vpn-Webmin.tar
```

## Running the container 
```
sudo docker run --name PPTPd-Service -d --privileged --cap-add=NET_ADMIN   --cap-add=SYS_MODULE   --sysctl="net.ipv4.conf.all.src_valid_mark=1"   --sysctl="net.ipv4.ip_forward=1"   --restart unless-stopped --env ROOT_PASSWORD="pass" --publish 10000:10000/tcp  --publish 1723:1723/tcp  --publish 1723:1723/udp  --publish 47:47/tcp  --publish 47:47/udp webmin/vpn
```

## Log into webmin and manage your server
```
https://hostname.or.ip:10000
(root:pass)
```
Root Password Change : /usr/share/webmin/changepass.pl /etc/webmin root pass
