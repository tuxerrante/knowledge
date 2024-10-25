# RHCSA

[**Sander van Vugt, RhatCertification**](https://www.youtube.com/c/Rhatcert/playlists)

* [OpenRHCE/RHCE\_Practice\_Exam\_01.rst.txt at master · texastwister/OpenRHCE](https://github.com/texastwister/OpenRHCE/blob/master/RHCE\_Practice\_Exam\_01.rst.txt)  
* [How To Set Up a Firewall Using FirewallD on CentOS 7](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-using-firewalld-on-centos-7)  
* [https://www.udemy.com/course/red-hat-system-administration-ii-rh134-sa2-rhel8](https://www.udemy.com/course/red-hat-system-administration-ii-rh134-sa2-rhel8)  
* [https://github.com/chlebik/rhcsa-practice-questions/](https://github.com/chlebik/rhcsa-practice-questions/)

## Users

Mostra tutti gli utenti 

	**lslogins**

‘**users**’ mostra solo quelli correntemente loggati

**w command** shows all users who are logged on the system and what they are doing.

**ACL**

	setfacl

	getfacl

pam\_tally2

\#\#  Account expiration and password policies  
chage \-l root

\#\# I valori di default per le nuove utenze sono in   
 /etc/login.defs

## Processes

### NICE level

La priorità va da \-20 a 19, più è alto il numero più bassa è la priorità.

ps \-axo pid,comm,nice |sort \-n \-k3

	nice \-n 5 sha1sum /dev/null

\---

L’uguale alla fine di un argomento di \-o mostra solo il risultato e non il titolo.

\# ps \-C rsyslogd \-o cmd=

/usr/sbin/rsyslogd \-n

To get info about threads:

          ps \-eLf

To get security info:

          ps \-eo euser,ruser,suser,fuser,f,comm,label

Print only the name of PID 42:

          ps \-q 42 \-o comm=

ps \-C syslogd \-o pid=

## CHROOT

A chroot jail is a way to isolate a process and its children from the rest of the system. It should only be used for processes that don't run as root, as root users can break out of the jail very easily.  
The idea is that you create a directory tree where you copy or link in all the system files needed for a process to run. You then use the chroot() system call to change the root directory to be at the base of this new tree and start the process running in that chroot'd environment. Since it can't actually reference paths outside the modified root, it can't perform operations (read/write etc.) maliciously on those locations.

It is NOT a security policy. Take care of the configuration.

Real jails can be enforced with [freebsd jails](https://en.wikipedia.org/wiki/FreeBSD\_jail\#Goals).  
[Understanding chroot Jail – The Geek Diary](https://www.thegeekdiary.com/understanding-chroot-jail/)  
[jailkit(8): utilities for jailing user/process \- Linux man page](https://linux.die.net/man/8/jailkit)

1. Download latest lux-release rpm from  
   wget [http://repo.iotti.biz/CentOS/7/noarch/lux-release-7-1.noarch.rpm](http://repo.iotti.biz/CentOS/7/noarch/lux-release-7-1.noarch.rpm)  
2. Install lux-release rpm:  
   \# rpm \-Uvh lux-release\*rpm  
3. Install jailkit rpm package:  
   \# yum install jailkit

Red Hat [How to set up Linux chroot jails](https://www.redhat.com/sysadmin/set-linux-chroot-jails)

## VIRTUAL DEVICES & LVM

pvs 	\# physical volumes  
vgs 	\# volume groups  
lvs 	\# local volumes

crea nuova partizione LVM da 100GB  
	fdisk /dev/sda  
Crea nuovo PV  
	 pvcreate /dev/sda3  
	 pvs  
Estendi il Volume Group  
	vgextend vg /dev/sda3  
Estendi LV con i PE disponibili (vgdisplay)	  
	lvextend \-L \+100G /dev/mapper/vg-lv\_root  
Resize del disco  
	\# resize2fs /dev/vg/lv\_root

\---  
\# yum install \-y kmod-kvdo vdo

## SELINUX

[https://access.redhat.com/documentation/en-us/red\_hat\_enterprise\_linux/8/html/using\_selinux/getting-started-with-selinux\_using-selinux](https://access.redhat.com/documentation/en-us/red\_hat\_enterprise\_linux/8/html/using\_selinux/getting-started-with-selinux\_using-selinux)

The standard access policy based on the user, group, and other permissions, known as Discretionary Access Control (DAC), does not enable system administrators to create comprehensive and fine-grained security policies, such as restricting specific applications to only viewing log files.

SELinux implements Mandatory Access Control (MAC). Every process and system resource has a special security label

SELinux policy rules are checked after DAC rules

SELinux contexts have several fields: user, role, type, and security level. The SELinux type information is perhaps the most important 

## TESTS

**1\.**  Configure your Host Name, IP Address, Gateway and DNS.

Host name: station.domain40.example.com

/etc/sysconfig/network

hostname=abc.com

hostname abc.com

IP Address:172.24.40.40/24

Gateway172.24.40.1

DNS:172.24.40.1

**2\.**  Add 3 users: harry, natasha, tom.

The requirements: The Additional group of the two users: harry, Natasha is the admin group. The user: tom's login shell should be non-interactive.

**3\.** Create a catalog under /home named admins. Its respective group is requested to be the admin group. The group users could read and write, while other users are not allowed to access it. The files created by users from the same group should also be the admin group.

**4\.** Configure a task: plan to run echo hello command at 14:23 every day.

**5\.**  Find the files owned by harry, and copy it to catalog: /opt/dir

**6\.**  Find the rows that contain abcde from file /etc/testfile, and write it to the file/tmp/testfile, and the sequence is requested as the same as /etc/testfile.

**7\.** Create a 2G swap partition which take effect automatically at boot-start, and it should not affect the original swap partition.

**8\.** Create a user named alex, and the user id should be 1234, and the password should be alex111.

**9\.**  Install a FTP server, and request to anonymous download from /var/ftp/pub catalog. (it needs you to configure yum direct to the already existing file server. )

4\. Share directory for NFS

To view the list of active zones

* A) firewall-cmd \--get-active-zones  
* B) firewall-get-active-zones  
* C) firewall-active-zones  
* D) none of the above

5\. To view the list of active zones

* A)firewall-cmd \--get-active-zones  
* B)firewall-get-active-zones  
* C) firewall-active-zones  
* D) none of the above

6\. Command to check selinux mode

* A) getenforce  
* B) getselinux  
* C) selinuxdisplay  
* D) none of the above

7\. Command to reduce volume group size

* A) vgreduce  
* B) vgchange  
* C) vgless  
* D) none of the above

8\. Command to create a user home directory

* A) useradd \-k /dirname/username user  
* B) useradd \-h /dirname/username user  
* C) useradd \-d /dirname/username user  
* D) nono of above

9\. Umask value 011 for files

* A) user has rw group & other have rx  
* B) all has rw permission  
* C) user has rwx group & other have rx  
* D) none of the above

10\. command to extend lvm

* A) lvextend  
* B) lvmod  
* C) lvchange  
* D) none of the above

11\. Which of the following command can be used to change the user password?

* A) User can’t change the password  
* B) passwd  
* C) passd  
* D) pwd

12\. The permission \-rwxr-sr– represented in octal expression will be

* A) 777  
* B) 2766  
* C) 2744  
* D)2754

13\. The command ‘disown \-r’

* A) removes all jobs  
* B) removes all running jobs  
* C) marks jobs to not receive SIGHUP when bash exits  
* D) marks all jobs

14\. Command to set selinux permissive mode

* A) setenforce 0  
* B) setenforce permissive  
* C) setenforce enforce  
* D) none of the above

15\. Which command can create environment variable?

* A) export  
* B) set  
* C) read  
* D) none

16\. Command to show hidden files and directories

* A) dir \-a  
* B) dir \-h  
* C) ls \-a  
* D) ls \-l

17\. The directory /media is the

* A) mount point for removable media  
* B) mount point for filesystem  
* C) both (a) and (b)  
* D) none of the mentioned

18\. Which command is used to set limits on file size  
A) fsize

* B) flimit  
* C) ulimit  
* D)usize

19\. Samba configuration file path

* A) /etc/samba/smb.conf  
* B) etc/smb.conf  
* C) /etc/samba.conf  
* D) none of the above

20\. Which command prints the directory stack?

* A) cd  
* B) dirs  
* C) popd  
* D) pushd

