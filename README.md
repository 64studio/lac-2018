# Linux Audio Conference 2018 - PDK Notes

## Install PDK

```bash
sudo apt-get install apt-transport-https
echo "deb https://apt.64studio.net stretch main" | sudo tee /etc/apt/sources.list.d/64studio.list
wget -qO - https://apt.64studio.net/public-key.asc | sudo apt-key add -
sudo apt-get update
sudo apt-get install pdk pdk-mediagen
```

## APT Repository key

- Make email apt@your-domain
- Do not set a passcode

```bash
sudo apt-get install rng-tools
sudo rngd -r /dev/urandom
gpg --gen-key
```

## Download PDK project sourcecode

```bash
~$ pdk workspace create pideck
~$ cd pideck/
~$ git remote add github https://github.com/pideck/pideck-distro.git
~/pideck$ git pull github master
~/pideck$ pdk channel update
~/pideck$ pdk pull components
```

## Build image

```
~/pideck$ pdk download pideck.xml

~/pideck$ make closure

~/pideck$ make image
```