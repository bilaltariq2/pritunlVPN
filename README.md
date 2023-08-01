# Getting started with pritunl VPN
## 1. VPN Overview
> Pritunl is the best open source alternative to other commercial vpn products.
## 2. VPN Configuration
> **VPN Clients:** [OpenVPN, Wireguard]<br>
> **Authentication Method:** [Username/Password, 2FA]
## 3. VPN Server Deployment
Pritunl supports different Linux distribtutions.<br>
***To install Pritunl VPN on Ubuntu 20.04:***
```bash
sudo tee /etc/apt/sources.list.d/mongodb-org-6.0.list << EOF
deb https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/6.0 multiverse
EOF

sudo tee /etc/apt/sources.list.d/pritunl.list << EOF
deb https://repo.pritunl.com/stable/apt focal main
EOF

sudo apt --assume-yes install gnupg
wget -qO- https://www.mongodb.org/static/pgp/server-6.0.asc | sudo tee /etc/apt/trusted.gpg.d/mongodb-org-6.0.asc
gpg --keyserver hkp://keyserver.ubuntu.com --recv-keys 7568D9BB55FF9E5287D586017AE645C0CF8E292A
gpg --armor --export 7568D9BB55FF9E5287D586017AE645C0CF8E292A | sudo tee /etc/apt/trusted.gpg.d/pritunl.asc
sudo apt update
sudo apt --assume-yes install pritunl mongodb-org
sudo systemctl start pritunl mongod
sudo systemctl enable pritunl mongod
```
***To install Pritunl VPN on Ubuntu 22.04:***
```bash
sudo tee /etc/apt/sources.list.d/mongodb-org-6.0.list << EOF
deb https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/6.0 multiverse
EOF

sudo tee /etc/apt/sources.list.d/pritunl.list << EOF
deb https://repo.pritunl.com/stable/apt jammy main
EOF

sudo apt --assume-yes install gnupg
wget -qO- https://www.mongodb.org/static/pgp/server-6.0.asc | sudo tee /etc/apt/trusted.gpg.d/mongodb-org-6.0.asc
gpg --keyserver hkp://keyserver.ubuntu.com --recv-keys 7568D9BB55FF9E5287D586017AE645C0CF8E292A
gpg --armor --export 7568D9BB55FF9E5287D586017AE645C0CF8E292A | sudo tee /etc/apt/trusted.gpg.d/pritunl.asc
sudo apt update
sudo apt --assume-yes install pritunl mongodb-org
sudo systemctl start pritunl mongod
sudo systemctl enable pritunl mongod
```
After installing no setup is necessary, simply open the web interface at https://SERVER_IP/ in your web browser.<br>
To get the server IP
```bash
ip addr
```
To get the default password
```bash
sudo pritunl default-password
```
## 4. Post Installation Seteup
Once you are successfully logged in, you can either edit the following details or setup them later:
+ Username
+ New Password
+ Public IP Address
+ Web Console Port
If you good to go, simply click **Save**
