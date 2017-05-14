## Setup non-root admin user

Change root password
```
passwd
```

Add the new user to the default sudo group, wheel:
```
adduser an_admin_user
passwd an_admin_user
usermod -a -G wheel an_admin_user
visudo
```

Look for this entry and uncomment to provide full sudo access to this group
```
 # %wheel  ALL=(ALL)       ALL
```

## Install/update base packages
```
yum update
```

## Install the Extra packages repository (EPEL - Extra Packages for Enterprise Linux)
```
sudo yum install epel-release
```
## Ensuring terminal ssh sessions don't time out on idle

Need to be sending keep alive packet every 30 seconds. Details at https://docs.oseems.com/general/application/ssh/disable-timeout#sthash.SFl3opZA.dpuf

```
sudo vi /etc/ssh/sshd_config
```

Add/modify the folowing lines in /etc/ssh/sshd_config

```
ClientAliveInterval 30
ClientAliveCountMax 9999
TCPKeepAlive yes
```


## Setting up SSH with deployment key for read-only access to repository
Instructions at: 
https://confluence.atlassian.com/bitbucket/set-up-ssh-for-git-728138079.html
https://confluence.atlassian.com/bitbucket/use-deployment-keys-294486051.html
1. General info: https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2

### Once all setup, test your deployment key access to repository using:
ssh -T git@bitbucket.org

(See https://confluence.atlassian.com/bitbucket/troubleshoot-ssh-issues-271943403.html)
