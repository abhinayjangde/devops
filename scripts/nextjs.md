apt-get update
apt-get upgrade -y
apt-get install git -y
apt-get install nginx -y
curl -sL https://deb.nodesource.com/setup_22.x -o nodesource_setup.sh
bash nodesource_setup.sh
apt install nodejs
npm install -g pm2@latest
pm2 startup
ufw enable
ufw allow ssh
ufw allow http
ufw allow https
ssh-keygen -t ed25519 -C "example@gmail.com"
cat ~/.ssh/id_ed25519.pub

nano /etc/nginx/sites-available/codebhaiya.com

```
server{
    listen 80;
    listen [::]:80;
    server_name codebhaiya.com www.codebhaiya.com;
    location / {
        proxy_pass http://localhost:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```
ln -s /etc/nginx/sites-available/codebhaiya.com /etc/nginx/sites-enabled/codebhaiya.com