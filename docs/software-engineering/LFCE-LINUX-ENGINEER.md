# LFCE \- LFS211- LINUX ENGINEER

[https://trainingportal.linuxfoundation.org/learn/course/linux-networking-and-administration-lfs211/](https://trainingportal.linuxfoundation.org/learn/course/linux-networking-and-administration-lfs211/linux-networking-concepts-and-review/linux-networking-concepts-and-review?page=18)

* [ghumman/lfce: Linux Foundation Certified Exam Preparation and Practice](https://github.com/ghumman/lfce)  
* [LFCE Exam Study Guide (Linux Foundation Certified Engineer)](https://ravikirans.com/lfce-linux-exam-study-guide/)  
* [https://learning.oreilly.com/videos/linux-foundation-certified/9780134774015/9780134774015-LFCE\_01\_01\_00](https://learning.oreilly.com/videos/linux-foundation-certified/9780134774015/9780134774015-LFCE\_01\_01\_00)  
* [LFCE: Installing Network Services and Configuring Automatic Startup at Boot \- Part 1](https://www.tecmint.com/installing-network-services-and-configuring-services-at-system-boot/)  
* [Linux Journey: Home](https://linuxjourney.com/)  
* [https://www.coursera.org/learn/real-time-cyber-threat-detection/home/welcome](https://www.coursera.org/learn/real-time-cyber-threat-detection/home/welcome)  
* [https://www.youtube.com/watch?v=D0Xob4DGbFQ](https://www.youtube.com/watch?v=D0Xob4DGbFQ)

[https://www.katacoda.com/courses/ubuntu/playground](https://www.katacoda.com/courses/ubuntu/playground)

## NETWORKING

less /etc/sysconfig/network-scripts/ifcfg-eth0

ifdown eth0; ifup eth0

ip a show eth0

ip route show  
ip route 

**nmcli** device show  	\# NetworkManager: dettagli per network devices  
nmcli \-f ip4.address device show enp1s0

nmtui 			\# interfaccia da terminale

se il networkmanager non gestisce connessioni allora forse lo sta facendo  
**networkctl** 

puoi verificare il manager anche tramite  
**netplan** get all  
*network:*  
  *renderer: NetworkManager*  
  *version: 2*

Esempi di configurazioni si trovano in /usr/share/doc/netplan/examples/

\# Change speed and mode of current enp0 interface  
sudo **ethtool** enp0s3 \--change speed 1000 duplex full

**DNS**  
**systemd-resolve \--status**

**systemd-resolve** \--set-dns=192.168.178.1 \--set-dns=10.34.168.6 \--interface=enp0s3

**nmcli** device show enp0

[https://phoenixnap.com/kb/linux-dig-command-examples](https://phoenixnap.com/kb/linux-dig-command-examples)   
**dig** \-x 172.217.14.238 		Reverse DNS  
dig google.com \-t A \+trace 		Type Address, trace the request

\# Ask server 8.8.4.4 the name google.com for records of type NameServer  
dig @8.8.4.4 google.com \-t NS \-c IN 	

nslookup google.com 8.8.8.8

**PING**  
load test  
ping \-f \-s 4096 IP

**TRACEROUTE**  
**traceroute** \-I IP 		usa ICMP per tentare bypass dei firewall

**NMAP**

**ARP** / **TELNET**  
telnet github.com 80

**openssl** s\_client \-connect github.com:443

**TCPDUMP**  
[https://danielmiessler.com/study/tcpdump/](https://danielmiessler.com/study/tcpdump/)

To capture packets with **tcpdump** for use with **wireshark**, use:  
$ sudo tcpdump \-i eth0 \-s 65535 \-w capture.pcap port 22

\# tcpdump \-nnvv \-i any net 127.0.0.1 and port 4200 and not 'tcp\[tcpflags\] \== tcp-syn'

**SERVER SIDE**  
SS  
**sudo ss \-ltp | grep httpd**

NETSTAT  
sudo netstat \-palute

**/etc/hosts**  
[man hosts\_access](https://linux.die.net/man/5/hosts\_access)

* **/proc/sys/net/ipv4/ip\_forward**  
  Allows for network traffic to be forwarded from one interface to another.  
* **/proc/sys/net/ipv4/conf/\*/accept\_redirects**  
  Accepting Internet Control Message Protocol (ICMP) redirects from a router to find better routes. This setting has the potential to be exploited by a malicious party to redirect your traffic.  
* **/proc/sys/net/ipv4/icmp\_echo\_ignore\_all**  
  Changing this setting will affect the host's visibility to ICMP ping packets.

To persistently enable changes you must use the **sysctl** command with its configuration file **/etc/sysctl.conf**.

sudo sysctl \--all |grep redirect

esempio:  
scrivi un log ogni volta che tentano la connessione ftp dal dominio .esempio.com  
hosts.deny  
vsftpd : 192.168.1. , .esempio.com : spawn /bin/echo  \`/bin/date\` access denied \>\> /var/log/vsftpd.log : deny

**NETCAT**  
netcat \-l 2000 		ascolta sul server sulla 2000  
netcat IP 2000		si connette

**TC Traffic Control**  
[https://linux.die.net/man/8/tc](https://linux.die.net/man/8/tc) 

**tc qdisc** add dev lo root netem loss random 40  
aggiunge una queue discilipline sul device lo tramite netEmulator che perderà il 40% dei pacchetti

ping localhost 						\#1  
sudo **tcpdump** \-nnvvS src 127.0.0.1 \-i lo 		\#2  
sudo tcpdump \-i lo \-nnvvS icmp

sudo tc qdisc show  
sudo **tc** qdisc delete lo root

**UDEV**  
ACPI is the Advanced Configuration and Power Interface standard ([Preexisting ACPI Specifications](http://www.uefi.org/acpi/specs)) by which the computer firmware (either the BIOS, for older machines, or its replacement, EUFI) can communicate what hardware is preinstalled in the computer to the operating system

udevadm test /sys/class/net/enp0s3  
udevadm info /sys/class/net/enp0s3

**TUN** e **TAP** sono driver che permettono la creazione di periferiche di rete virtuali. Rispetto alle comuni periferiche (ad es. eth0) che sono controllate direttamente dalle schede di rete, i [pacchetti](https://it.wikipedia.org/wiki/Pacchetto\_(reti)) spediti da o verso dispositivi TUN/TAP sono spediti da o verso programmi software. **TUN** è in grado di simulare una periferica di rete di tipo punto-punto e lavora con pacchetti di tipo [IP](https://it.wikipedia.org/wiki/Internet\_Protocol) mentre **TAP** è in grado di simulare un dispositivo Ethernet e logicamente utilizza i frame [Ethernet](https://it.wikipedia.org/wiki/Ethernet). 

**FILES**  
/etc/hostname 	hostname della macchina  
/etc/resolv.conf 	DNS  
/etc/network 		  
/etc/netplan/01..		Stesso risultato di ‘netplan get all’  
/usr/share/doc/ppp/examples/interfaces

### IFCONFIG

[https://www.computerhope.com/unix/uifconfi.htm](https://www.computerhope.com/unix/uifconfi.htm)

### FIREWALL

[https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-using-firewalld-on-centos-7](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-using-firewalld-on-centos-7)

### SSH

**pssh** \-H box \-H node1 \-H node2 "yum install \-y tmux bash-completion bash-completion-extras && mandb"

/etc/ssh/ssh\_config  
sudo apt install openssh-server → /etc/ssh/sshd\_config  
grep \-E “^\\w” /etc/ssh/sshd\_config

ssh-keygen \-f $HOME/.ssh/id\_rsa \-N 'supersecret' \-t rsa  
ssh-copy-id alex@IP

### DNS

[https://ns1.com/resources/dns-types-records-servers-and-queries](https://ns1.com/resources/dns-types-records-servers-and-queries)

host  
dig  
resolvectl query   
nslookup

DNS SERVER  
apt install \-y bind9 resolvconf  
systemctl start bind9  
**/etc/resolv.conf**  
**/etc/systemd/resolved.conf**  
**/etc/bind/named.conf** 

/etc/bind/named.conf.options  
options {  
    	listen-on port 53 { any; };  
    	allow-query   	{ any; };  
    	recursion   	yes;  
};

## SYSTEM SERVICES

[Understanding Systemd Units and Unit Files](https://www.digitalocean.com/community/tutorials/understanding-systemd-units-and-unit-files)

Systemd has a flexible configuration architecture that uses override and drop-in directories. The sequence in which systemd processes the configuration files is predictable and extensible. The common sequence is:

* The vendor-supplied unit file in **/usr/lib/systemd/\<service\>.service** or **/lib/systemd/system/\<service\>.service**.  
* Optional or dynamically-created unit files in the **/run/systemd/system/** directory.  
* Optional user-unit override files in the **/etc/systemd/system/** directory.  
* Optional user drop-in files in **/etc/systemd/system/\<service\>.d**.

**man 5 systemd-system.conf**  
When packages need to customize the configuration, they can install configuration snippets in **/usr/lib/systemd/\*.conf.d/**. Files in **/etc/** are reserved for the local administrator, who may use this logic to override the configuration files installed by vendor packages.

ES: manually launch ftp service  
\# /usr/sbin/vsftpd /etc/vsftpd/vsftpd.conf &

## YUM

yum provides \*/traceroute

## HTTP

ubuntu apache2  
centos httpd

/var/www/html 	siti  
/var/log/apache2 	access e error log

$ grep "^\\w" /etc/apache2/apache2.conf  
DefaultRuntimeDir ${APACHE\_RUN\_DIR}  
PidFile ${APACHE\_PID\_FILE}  
Timeout 300  
KeepAlive On  
MaxKeepAliveRequests 100  
KeepAliveTimeout 5  
User ${APACHE\_RUN\_USER}  
Group ${APACHE\_RUN\_GROUP}  
HostnameLookups Off  
ErrorLog ${APACHE\_LOG\_DIR}/error.log  
LogLevel warn  
IncludeOptional mods-enabled/\*.load  
IncludeOptional mods-enabled/\*.conf  
Include ports.conf  
AccessFileName .htaccess  
LogFormat "%v:%p %h %l %u %t \\"%r\\" %\>s %O \\"%{Referer}i\\" \\"%{User-Agent}i\\"" vhost\_combined  
LogFormat "%h %l %u %t \\"%r\\" %\>s %O \\"%{Referer}i\\" \\"%{User-Agent}i\\"" combined  
LogFormat "%h %l %u %t \\"%r\\" %\>s %O" common  
LogFormat "%{Referer}i \-\> %U" referer  
LogFormat "%{User-agent}i" agent  
IncludeOptional conf-enabled/\*.conf  
IncludeOptional sites-enabled/\*.conf

[http://httpd.apache.org/docs/2.2/mod/mod\_log\_config.html\#formats](http://httpd.apache.org/docs/2.2/mod/mod\_log\_config.html\#formats)

sudo **apachectl configtest**

[https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-apache-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-apache-on-ubuntu-14-04)

sudo vim /etc/apache2/sites-enabled/000-default.conf  
\<Directory "/var/www/html/get-only"\>  
   	**AuthType Basic**  
    	AuthName "Restricted Content"  
     	AuthUserFile /etc/apache2/secure.passwords  
     	Require valid-user  
\</Directory\>  
sudo systemctl restart apache2

[https://www.ibm.com/docs/en/aspera-on-demand/3.9?topic=appendix-enable-ssl-apache](https://www.ibm.com/docs/en/aspera-on-demand/3.9?topic=appendix-enable-ssl-apache)

[KVM forward ports to guests VM with UFW on Linux](https://www.cyberciti.biz/faq/kvm-forward-ports-to-guests-vm-with-ufw-on-linux/)

Rewrite flags [RewriteRule Flags \- Apache HTTP Server Version 2.4](https://httpd.apache.org/docs/2.4/rewrite/flags.html)  
Directory directives [https://httpd.apache.org/docs/2.4/mod/core.html\#allowoverride](https://httpd.apache.org/docs/2.4/mod/core.html\#allowoverride)

#### Create a new key and certificate with openssl

[https://www.katacoda.com/courses/ubuntu/playground](https://www.katacoda.com/courses/ubuntu/playground)

man 1 req  
openssl req \-x509 \-newkey rsa:2048 \-keyout my.key \-out mycert.crt  
vim sites-enabled/000-default.conf  
cp sites-available/default-ssl.conf sites-enabled/  
echo "127.0.0.1 alex.com" \>\> /etc/hosts  
curl \-Ik https://alex.com  
HTTP/1.1 200 OK

## MAIL

[https://doc.dovecot.org/configuration\_manual/](https://doc.dovecot.org/configuration\_manual/)  
[http://www.postfix.org/postconf.5.html](http://www.postfix.org/postconf.5.html)

**/etc/postfix/main.cf** 

only a few mail parameters need to be altered in **/etc/postfix/main.cf**. 

* The domain name to use for outbound mail (**myorigin**).  
* The domains to receive mail for (**mydestination**).  
* The clients to allow relaying of mail (**mynetworks**).  
* The destinations to relay mail to (**relay\_domains**).  
* The delivery method, indirect or direct (**relayhost**). 

The **postconf** command can be used to customize **/etc/postfix/main.conf**:

**\# postconf \-e 'inet\_interfaces \= all'**  
**\# postconf \-e "mynetworks\_style \= subnet"**

\~\# vim /etc/postfix/master.cf  
\~\# vim /etc/postfix/main.cf  
\~\# vim /etc/aliases

## PROXY

[https://en.wikipedia.org/wiki/Reverse\_proxy](https://en.wikipedia.org/wiki/Reverse\_proxy)

[http://www.squid-cache.org/Versions/v6/cfgman/](http://www.squid-cache.org/Versions/v6/cfgman/)  
[SquidFaq/SquidAcl \- Squid Web Proxy Wiki](https://wiki.squid-cache.org/SquidFaq/SquidAcl)

[https://wiki.squid-cache.org/ConfigExamples/Intercept/LinuxRedirect](https://wiki.squid-cache.org/ConfigExamples/Intercept/LinuxRedirect)

Squid can also parse and check its syntax with a built-in syntax checker:  
**\# squid \-k parse**

The first match wins. Therefore, start your ACLs with the most specific options in the beginning.  
\# grep "^\\w" /etc/squid/squid.conf  
acl localnet src 0.0.0.1-0.255.255.255    \# RFC 1122 "this" network (LAN)  
acl localnet src 192.168.0.0/16   	 \# RFC 1918 local private network (LAN)

acl SSL\_ports port 443  
acl Safe\_ports port 80   	 \# http  
acl Safe\_ports port 21   	 \# ftp  
acl Safe\_ports port 443   	 \# https

http\_access deny \!Safe\_ports  
http\_access deny CONNECT \!SSL\_ports  
http\_access allow localhost manager  
http\_access deny manager  
\-------

## NFS

\# groupadd \-g 42000 share  
\# chown nfsnobody /home/export  
\# chgrp share \-R /home/export  
\# chmod \-R 2770 /home/export  
\# usermod \-aG share student  
\# usermod \-aG share root

\# cat \<\<EOF \>\>**/etc/exports**  
\> /home/export  127.0.0.1/32(rw) 192.168.0.0/16(ro)  
\> EOF

systemctl restart nfs-server  
mount 127.0.0.1:/home/export /mnt/my-nfs

man exports

## SAMBA

\# apt install samba smbclient

man **smb.conf**

cat \<\<EOF \>\>/etc/samba/smb.conf  
\[lab13-3\]  
  guest ok \= yes  
  read only \= yes  
  path \= /home/export/cifs  
EOF

smbclient \-L localhost  
smbclient //localhost/lab13-3

\-- PRIVATE ACCESS EXAMPLE  
cat \<\<EOF \>\>/etc/samba/smb.conf  
\[lab-private\]  
  path \= /home/export/private  
  valid users \= alex  
  read only \= no  
  public \= no  
EOF

\# chown \-R alex /home/export/private/my-secret  
\# smbpasswd \-a alex  
\# systemctl restart smbd.service  
\# smbclient \-L localhost  
\# smbclient \-U alex //localhost/lab-private  
smb: \\\> get my-secret

\-- **ETC/FSTAB**  
man systemd.mount

127.0.0.1:/home/export/nfs /home/share/nfs nfs x-systemd.automount,x-systemd.idle-timeout=10,noauto,\_netdev  
0 0

//localhost/mainexports /home/share/cifs cifs credentials=/root/smbfile,x-systemd.automount,x-systemd.idle-timeout=10,noauto,\_netdev 0 0

## SECURITY

**SELINUX**  
[Basic SELinux Troubleshooting in CLI](https://access.redhat.com/articles/2191331)

**APPARMOR**  
[https://wiki.debian.org/AppArmor/HowToUse](https://wiki.debian.org/AppArmor/HowToUse)  
/etc/apparmor.d  
apparmor\_status

**PAM**  
Framework for authentication called Pluggable Authentication Module (PAM).

**CHROOT**

[https://us-cert.cisa.gov/ncas/alerts](https://us-cert.cisa.gov/ncas/alerts)

nmap  
tcpdump  
snort

**FIREWALL**  
netfilter  
nftables

When traffic comes to a **libwrap**\-enabled daemon, those two files are consulted

- /etc/hosts.allow  
- /etc/hosts.deny

* The **netfilter** firewall consists of *tables*.  
* Tables consist of ***chains***.  
* Chains have a default *policy*.  
* Chains consist of *rules*.  
* Rules consist of a *match criteria* and a *target*.

- **filter** table deals with packets bound for the local machine, being routed through the machine, or packets generated by processes on the machine.  
  chains: forward, input, output  
- **NAT** table for traffic creating a new network connection. Chains: prerouting, output, postrouting  
- **mangle** for all network packets rules: prerouting, input, output, forward, postrouting

sudo **ufw** app list  
sudo ufw show listening   
		raw

**IPTABLES**  
[**7.4. Regole FORWARD e NAT**](http://web.mit.edu/rhel-doc/4/RH-DOCS/rhel-sg-it-4/s1-firewall-ipt-fwd.html)

man iptables  
man iptables-extensions

**iptables** \--list-rules  
	  \--list  
iptables \--list INPUT \--type mangle \-v

Targets: ACCEPT, DROP, REJECT 

\# Con drop la connessione rimane in attesa, con reject chiusa subito  
iptables \-A INPUT \--proto tcp \--dport 80 \--jump DROP

iptables \-A INPUT \--proto tcp \--dport 8080 \--jump REJECT \--reject-with icmp-net-prohibited

\# apt install iptables-persistent  
\# iptables-save

To enable **DNAT redirect** (DMZ ecc):  
echo 1 \> /proc/sys/net/ipv4/ip\_forward  
/etc/sysctl.conf  \-----\> net.ipv4.ip\_forward=1  \# Rileggi le conf con **sysctl \-p** /etc/sysctl.conf

**MASQUERADE**  
This target is only valid in the nat table, in the POSTROUTING chain.  It should only be used with dynamically assigned IP (dialup) connections: if you have a static IP address, you should use the SNAT target.  
\# iptables \-t nat \-A POSTROUTING \-o eth1 \! \-d 192.168.12.0/24 \-j MASQUERADE

Accettando i pacchetti inoltrati tramite il dispositivo IP interno, si abilita la comunicazione tra i nodi LAN; tuttavia essi non sono ancora abilitati a comunicare esternamente con Internet. Per abilitare i nodi LAN con indirizzi IP privati alla comunicazione con le reti pubbliche esterne, configurate il firewall per l'*IP masquerading*, il quale maschera le richieste provenienti dai nodi LAN con l'indirizzo IP dei dispositivi esterni del firewall  
iptables \-A FORWARD \-i eth1 \-j ACCEPT  
iptables \-A FORWARD \-o eth1 \-j ACCEPT  
iptables \-t nat \-A POSTROUTING \-o eth0 \-j MASQUERADE

**Traffic redirect** through Squid  
iptables \-t nat \-A PREROUTING \-s $SQUIDIP \-p tcp \--dport 80 \-j ACCEPT  
iptables \-t nat \-A PREROUTING \-p tcp \--dport 80 \-j REDIRECT \--to-port $SQUIDPORT  
iptables \-t nat \-A POSTROUTING \-j MASQUERADE

**LOG** connections  
iptables \-A INPUT \-i lo \-p tcp \--dport 4200 \--destination localhost \-m state NEW \-j LOG \--log-level info \--log-prefix “NEW CON LOCAL “

journactl \-f

**block** all other traffic   
\# iptables \-P INPUT DROP

## CONTAINERS

[https://book.hacktricks.xyz/pentesting/2375-pentesting-docker](https://book.hacktricks.xyz/pentesting/2375-pentesting-docker)

Note sul corso

[https://trainingportal.linuxfoundation.org/learn/course/linux-networking-and-administration-lfs211/network-security/knowledge-check?page=1](https://trainingportal.linuxfoundation.org/learn/course/linux-networking-and-administration-lfs211/network-security/knowledge-check?page=1)  
no knowledge check

