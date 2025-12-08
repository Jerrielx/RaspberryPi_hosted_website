# Project Notes

## Nginx Setup

sudo apt install nginx -y
systemctl status nginx

install - be apt att installera paket
systemctl - verktyg för att styra systemtjänster
status nginx - status för tjänsten nginx
sudo systemctl stop nginx     # stoppa servern
sudo systemctl start nginx    # starta servern
sudo systemctl restart nginx  # starta om servern

sudo nano /etc/nginx/sites-available/my_website
server {
    listen 80;
    listen [::]:80;

    server_name _;

    root /home/jerrych/projects/my_website;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
listen 80; → Listen on port 80, the default for HTTP.
listen [::]:80; → Same but for IPv6.
server_name _; → default server for any hostname
root → where your site lives (your project folder).
index index.html; → file that will be served when user visits /.
try_files ... → if file not found, return 404.
/etc/nginx/sites-available/my_website   <-- real file
/etc/nginx/sites-enabled/my_website     <-- symlink (shortcut)
sudo ln -s /etc/nginx/sites-available/my_website /etc/nginx/sites-enabled/my_website
sudo nginx -t
sudo systemctl reload nginx

## basic html config
index.html
<!DOCTYPE html>
<html>
  <body>
    <h1>Hello from Jerry’s Raspberry Pi!</h1>
    <p>If you see this page, Nginx is correctly serving your website.</p>
  </body>
</html>

## rpi permission issue - allow permission on my folder
chmod o+x /home/jerrych
chmod = change mode
o = others, +x = allow execute on directory

## git commands
git init
git add .
git commit -m "commit message"
git brach -M main
git remote add origin htts://github.com/Jerrielx/...
git push -u origin main

## git ssh
ssh-keygen -t ed25519 -C "email@.com"

## raspberry pi notes
sudo apt update
ssh jerrych@ip
ssh jerrych@jerrypi.local
sudo reboot
sudo shutdown - stänger av rpi helt
exit - avsluta ssh

