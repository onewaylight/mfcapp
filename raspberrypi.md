
pm2 start app.js
pm2 stop app.js
pm2 monit
pm2 log


sudo pm2 startup systemd -u pi
sudo systemctl enable pm2-pi
```
$ sudo pm2 startup            # enable PM2 to start at system boot
$ sudo pm2 startup systemd    # or explicitly specify systemd as startup system 
$ sudo pm2 save               # save current process list on reboot
$ sudo pm2 unstartup          # disable PM2 from starting at system boot
$ sudo pm2 update	            # update PM2 package
```
