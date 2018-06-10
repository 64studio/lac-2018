# Linux Audio Conference 2018 - PDK Notes

## Install PDK

```bash
sudo apt install apt-transport-https
echo "deb https://apt.64studio.net stretch main" | sudo tee /etc/apt/sources.list.d/64studio.list
wget -qO - https://apt.64studio.net/archive-keyring.asc | sudo apt-key add -
sudo apt update
sudo apt install pdk pdk-mediagen rng-tools
```
(ignore service failing to start with "Cannot find a hardware RNG device to use.")

## APT Repository key

- Make email apt@your-domain
- Do not set a passphrase (you will be prompted twice)

```bash
sudo rngd -r /dev/urandom
gpg --gen-key
```

## Download PDK project 'PiDeck'

```bash
pdk workspace create pideck
cd pideck/
git remote add github https://github.com/pideck/pideck-distro.git
git pull github master
pdk channel update
pdk pull components
pdk download pideck.xml
```

## Modify APT repo key email address, modify project Makefile, modify postinst script

```bash
nano pideck.xml
nano Makefile
nano postinst.sh
```

## Commit changes and build image

```bash
pdk commit -m "A note about my changes"
make local
make image
```
