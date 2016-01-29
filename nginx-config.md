## Install nginx
sudo yum install -y nginx

## Make Nginx start when your server starts
sudo systemctl enable nginx

## Start nginx
sudo systemctl start nginx

## Open up the firewall ports for HTTP and HTTPS
sudo firewall-cmd --permanent --zone=public --add-service=http

sudo firewall-cmd --permanent --zone=public --add-service=https

sudo firewall-cmd --reload


## Nginx common commands
sudo systemctl start nginx

sudo systemctl stop nginx

sudo systemctl reload nginx

sudo systemctl restart nginx
