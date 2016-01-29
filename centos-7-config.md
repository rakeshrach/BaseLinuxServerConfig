## Setup non-root admin user

%passwd
(change root password)

%adduser admin
%passwd admin

%usermod -a -G wheel admin
%visudo

(Look for this entry and uncomment)
 # %wheel  ALL=(ALL)       ALL

## Install/update base packages
%yum update

## Install the Extra packages repository (EPEL - Extra Packages for Enterprise Linux)
%sudo yum install epel-release

## Ensuring terminal ssh sessions don't time out on idle
Need to be sending keep alive packet every 30 seconds. Details at https://docs.oseems.com/general/application/ssh/disable-timeout#sthash.SFl3opZA.dpuf

%sudo vi /etc/ssh/sshd_config

Add/modify the folowing lines in /etc/ssh/sshd_config
ClientAliveInterval 30
ClientAliveCountMax 9999
TCPKeepAlive yes
