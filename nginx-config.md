## Install nginx
```
sudo yum install -y nginx
```
## Make Nginx start when your server starts
```
sudo systemctl enable nginx
```
## Start nginx
```
sudo systemctl start nginx
```

## Open up the firewall ports for HTTP and HTTPS
```
sudo firewall-cmd --permanent --zone=public --add-service=http
sudo firewall-cmd --permanent --zone=public --add-service=https
sudo firewall-cmd --reload
```

## Nginx common commands
```
sudo systemctl start nginx
sudo systemctl stop nginx
sudo systemctl reload nginx
sudo systemctl restart nginx
```

## Configure nginx as reverse proxy for node apps
```
sudo vi /etc/nginx/nginx.conf
```

Find the line where ‘location /‘ is defined and replace with:
```
location / {
        proxy_pass http://APP_PRIVATE_IP_ADDRESS:8080;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
```

Restart Nginx and enable it to start on boot
```
sudo systemctl restart nginx
sudo systemctl enable nginx
```


## Setting up SSH with deployment key for read-only access to repository
Full instructions at: 
https://confluence.atlassian.com/bitbucket/set-up-ssh-for-git-728138079.html
https://confluence.atlassian.com/bitbucket/use-deployment-keys-294486051.html
1. General info: https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2

Once all setup, test your deployment key access to repository using:
```
ssh -T git@bitbucket.org
```
(See https://confluence.atlassian.com/bitbucket/troubleshoot-ssh-issues-271943403.html)
