# Directadmin-1.53-nulled

P/s: Note that this version only works on Centos 7 64bit

Setting:

[root@vps190651 ~]# yum -y install nano wget perl

[root@vps190651 ~]# wget https://raw.githubusercontent.com/ghost0506e/directadmin-1.53-nulled/master/setup.sh

[root@vps190651 ~]# chmod +x setup.sh

[root@vps190651 ~]# ./setup.sh

Enter the ID and lic id numbers any you like

Note after the installation is complete, it will not run, then declare the port for it to command

[root@vps190651 ~]# firewall-cmd --zone=public --add-port=2222/tcp --permanent

[root@vps190651 ~]# firewall-cmd --zone=public --add-port=21/tcp --permanent

[root@vps190651 ~]# firewall-cmd --zone=public --add-port=80/tcp --permanent

[root@vps190651 ~]# firewall-cmd --zone=public --add-port=25/tcp --permanent

[root@vps190651 ~]# firewall-cmd --reload

[root@vps190651 ~]# systemctl restart directadmin

[root@vps190651 conf]# cd /usr/local/directadmin/conf/

[root@vps190651 conf]# service directadmin stop

[root@vps190651 conf]# rm -rf /usr/local/directadmin/conf/license.key

[root@vps190651 conf]# wget -O /usr/local/directadmin/conf/license.key https://www.plesk.com.vn/license.key

[root@vps190651 conf]# chmod 600 /usr/local/directadmin/conf/license.key

[root@vps190651 conf]# chown diradmin:diradmin /usr/local/directadmin/conf/license.key

[root@vps190651 conf]# ifconfig eth0:100 103.237.147.148 netmask 255.0.0.0 up

[root@vps190651 conf]# echo 'DEVICE=eth0:100' >> /etc/sysconfig/network-scripts/ifcfg-eth0:100

[root@vps190651 conf]# echo 'IPADDR=103.237.147.148' >> /etc/sysconfig/network-scripts/ifcfg-eth0:100

[root@vps190651 conf]# echo 'NETMASK=255.0.0.0' >> /etc/sysconfig/network-scripts/ifcfg-eth0:100

[root@vps190651 conf]# service network restart

[root@vps190651 conf]# /usr/bin/perl -pi -e 's/^ethernet_dev=.*/ethernet_dev=eth0:100/' /usr/local/directadmin/conf/directadmin.conf

[root@vps190651 conf]# service directadmin start
