# Installing Node.js
(Full details at https://www.digitalocean.com/community/tutorials/how-to-set-up-a-node-js-application-for-production-on-centos-7)


Npm has a dependency on git
```
sudo yum install git
```

Download latest node dist
Get latest link from https://nodejs.org/en/download
```
cd ~
wget https://nodejs.org/dist/v4.2.4/node-v4.2.4-linux-x64.tar.gz
```


Extract the tar archive you just downloaded into the node directory
```
mkdir node
tar xvf node-v*.tar.gz --strip-components=1 -C ./node
```

Remove the original tar file 
```
rm -rf node-v*
```

Configure the global prefix of npm,
Where npm will create symbolic links to installed Node packages, to somewhere that it's in your default path. We'll set it to /usr/local
```
mkdir node/etc
echo 'prefix=/usr/local' > node/etc/npmrc
```

Now we're ready to move the node and npm binaries our installation location. We'll move it into /opt/node
```
sudo mv node /opt/
```

Make root the owner of the file
```
sudo chown -R root: /opt/node
```

Create symbolic links of the node and npm binaries in your default path. We'll put the links in /usr/local/bin
```
sudo ln -s /opt/node/bin/node /usr/local/bin/node
sudo ln -s /opt/node/bin/npm /usr/local/bin/npm
```

Dy default, /usr/local/bin is excluded from PATH when sudo is used. To change that, open the sudoers file
```
sudo visudo
```

Find the line that specifies Defaults secure_path and add :/usr/local/bin to the end of it. It should look like this when you're done:
```
Defaults    secure_path = /sbin:/bin:/usr/sbin:/usr/bin:/usr/local/bin
```

Verify that Node is installed 
```
node -v
```
