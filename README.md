## safe-rm for Void Linux

https://launchpad.net/safe-rm

Safe-rm is a safety tool intended to prevent the accidental deletion of important files by replacing* /bin/rm with a wrapper, which checks the given arguments against a configurable list of exclusions for files and directories that should never be removed.

```bash
rm -rf /
safe-rm: Skipping /.
```

Keep in mind that we're not replacing /bin/rm by itself. We're just pointing to a different binary in /usr/local/bin. This way we will keep /bin/rm from coreutils so it can be updated or used to bypass safe-rm. You can also decide wheter you want to use /bin/rm or /bin/safe-rm depending on your use-case.

## Installation

### manual

```bash
sudo xbps-install cargo make wget
wget https://launchpad.net/safe-rm/trunk/1.1.0/+download/safe-rm-1.1.0.tar.gz
tar -xvf safe-rm-1.1.0.tar.gz
cd safe-rm-1.1.0
make
sudo cp target/release/safe-rm /usr/bin/
sudo wget -O /etc/safe-rm.conf https://raw.githubusercontent.com/c0m4r/void-safe-rm/main/srcpkgs/safe-rm/files/safe-rm.conf
sudo ln -s /usr/bin/safe-rm /usr/local/bin/rm
```

### xbps

```bash
cd void-packages/srcpkgs
git clone https://github.com/c0m4r/void-safe-rm.git safe-rm
./xbps-src pkg safe-rm
sudo xbps-install --repository hostdir/binpkgs safe-rm
sudo ln -s /usr/bin/safe-rm /usr/local/bin/rm
```

## Configuration

1. Make sure your $PATH contains /usr/local/bin before /usr/bin
2. Edit /etc/safe-rm.conf to add or remove protected paths
