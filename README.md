## safe-rm for void-linux

## xbps

```
cd void-packages/srcpkgs
git clone https://github.com/c0m4r/void-linux-safe-rm.git safe-rm
./xbps-src pkg safe-rm
sudo xbps-install --repository hostdir/binpkgs safe-rm
sudo ln -s /usr/bin/safe-rm /usr/local/bin/rm
```

## manual

```
sudo xbps-install cargo make wget
wget https://launchpad.net/safe-rm/trunk/1.1.0/+download/safe-rm-1.1.0.tar.gz
tar -xvf safe-rm-1.1.0.tar.gz
cd safe-rm-1.1.0
make
sudo cp target/release/safe-rm /usr/bin/
sudo wget -O /etc/safe-rm.conf https://raw.githubusercontent.com/c0m4r/void-linux-safe-rm/main/srcpkgs/safe-rm/files/safe-rm.conf
sudo ln -s /usr/bin/safe-rm /usr/local/bin/rm
```
