# Linux Audio Conference 2018 - PDK Notes

## Install PDK

```bash
sudo apt install apt-transport-https
echo "deb https://apt.64studio.net stretch main" | sudo tee /etc/apt/sources.list.d/64studio.list
wget -qO - https://apt.64studio.net/public-key.asc | sudo apt-key add -
sudo apt update
sudo apt install pdk pdk-mediagen
```

## APT Repository key

- Make email apt@your-domain
- Do not set a passphrase

```bash
sudo apt install rng-tools
```
(ignore service failing to start with "Cannot find a hardware RNG device to use.")
```
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
```

## Build image

```
pdk download pideck.xml
make closure
make image
```
