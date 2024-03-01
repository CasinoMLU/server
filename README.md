# server
```
git clone https://github.com/CasinoMLU/server/tree/main
```
```
cd server
```
```
cargo build --release
```
```
cp src/target/server /bin/server
```

### /var/www
```
mkdir /var/www
```
```
adduser srv --shell=/bin/false --no-create-home
```

### systemd service
```
wget https://raw.githubusercontent.com/CasinoMLU/server/main/server.service
```
```
mv server.service /etc/systemd/system/server.service
```
```
systemctl start server.service
```
```
systemctl enable server.service
```
### sneaky way for more mem on vServer
```
dd if=/dev/zero of=/swapfile bs=1M count=8192 
```
```
chmod 0600 /swapfile
```
```
mkswap /swapfile 
```
```
swapon /swapfile 
```
### certbot
```
dnf install -y epel-release
```
```
dnf install -y snapd
```
```
systemctl enable --now snapd.socket
```
```
ln -s /var/lib/snapd/snap /snap
```
```
snap install --classic certbot
```
```
ln -s /snap/bin/certbot /usr/bin/certbot
```
