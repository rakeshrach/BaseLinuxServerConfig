## Install PM2

```
sudo npm install pm2@latest -g
```

Install the ‘pm2 startup’ subcommand to generate and configure a startup script to launch PM2 and its managed processes on server boots.
```
sudo pm2 startup systemd
```

Setup NODE_ENV variable to “production” 
```
sudo vi /etc/systemd/system/pm2.service
```

Add the lines to pm2.service
```
Environment=NODE_ENV=production
```
(More info on this at http://expressjs.com/en/advanced/best-practice-performance.html#proxy)


Reload changes to systemd
```
sudo systemctl daemon-reload
sudo systemctl restart pm2.service
```

## PM2 deploy

```
sudo pm2 deploy ecosystem.json production setup --force
sudo pm2 deploy ecosystem.json production update --force
sudo pm2 deploy ecosystem.json production --force
```