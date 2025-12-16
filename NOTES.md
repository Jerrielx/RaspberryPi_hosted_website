# Raspberry Pi project notes
# Author: Jerry Cheung
# File: NOTES.MD
# Date: 2015-12-16

# Project Notes

## Linux
sudo nmcli device wifi connect "YourSSID" --ask
nmcli - network manager command line interface
curl -fsSL https://tailscale.com/install.sh | sh
curl - program that downloads data from internet
-f fail silently on server errors, -s silent mode
-S show error if something fails, -L follow redirects(if URL changes)

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

## HTML
<html>...</html> - whole page
<head>...</head> - info about the page(title, encoding)
<body>...</body> - everything visible
<h1>, <h2>, <h3> - headings(big -> smaller)
<p> - paragraph, <u1><li> - bullest list

<meta charset="UTF-8"/> - what character encoding the page uses
<a href="link">link</a>
<a hred="link" target="_blank">Github</a>
a = anchor (a hyperlink) - creates a clickable link
href="" - tells the browser where to go when link is clicked
"_blank" - open in a new tab
<em> - Italics(semantic)
<ul> - unordered list(bullet points), <li> - list item
<br> - go to next line, 
&nbsp; = non-breaking space, &lt; = <, &gt; = >, &amp; = &
<link rel="stylesheet" href="style.css">
<link> - include another file as part of this page
rel - relation
<div class = "container"> - a box that groups elements together

## CSS
#RRGGBB 00(0%) -> FF(100%), #f5f5f5-light gray, #ffffff-white
.container{...} - class selector
max-width: 800px - limits width, margin: 0 auto - centers the container horizontally
padding: 20px - add space between text and edges

## Tailscale commends
sudo tailscale up
tailscale ip -4
tailscale status
sudo tailscale funnel --bg 80 - expose my pi's port 80 to internet
--bg : background configuration

## Mirroring cafe website
curl -s https://bistrograndenstockholm.se/
grep -oE 'https://impro\.usercontent\.one[^"]+'
sed 's/&amp;/\&/g'  replace every &amp; with &
head -n 20
  curl : downloads the raw html of the homepage, -s = silent(no progress bar)
  grep searches text for lines that match a pattern
  -o only print the matched part, -E extended regular expressions
  [^"]+ grab until quote
  sed stream editor, s/old/new/ = replace old with new, g = globally
  head prints the beginning of the input, -n 20 print the first 20 lines

