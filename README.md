# [install-discord-kali-linux-dpkg](https://github.com/ErfanRFZ/install-discord-kali-linux-dpkg)

For installing discord on kali linux we have 3 option -dpkg -snapcraft -flatpak the option for `Debian/Ubuntu` is `-dpkg` in this repository you can fix all errors and fully install discord.

## Step 1| Removing previous version of Discord
### snap
if you installed Discord with `snap` run this command to remove it:
```bash
snap remove discord
```

* consider that if you are not in `sudo mode` run the above command with starting sudo

## Step 2| Prepare for installing
### Part1:
so if you uninstall Discord from your system or you don't have it currently need to run some commands to prepare your linux to install the app
 first run this commands in order(just in case):
 ```bash
sudo apt update
sudo apt upgrade
 ```
* now run this command for surely you system doesn't have any side problems.
```bash
sudo apt --fix-broken install
```
  * if you get any message according to Discord does not fully install remove it or not like this
  ```
  discord
1 not fully installed.
Need to clear memory.
After this operation, 189 mb will be free disk space.
Do you want to continue? [Y/n]
```
* Enter `y` to remove it.

### Part2:
now you might get errors for installing Discord with `dpkg` that you need to install some packages that you dont have them on your system like:
```
This package is uninstallable
Dependency is not satisfiable: libgconf-2-4
Dependency is not satisfiable: libc++1
Dependency is not satisfiable: libappindicator1
```
* for fix this issue you need to install them by following commands down below (in order):
```bash
sudo apt --fix-broken install
sudo apt-get install libgconf-2-4

sudo apt --fix-broken install
sudo apt-get install libc++1

sudo apt --fix-broken install
sudo apt-get install libappindicator1

```

## Step 3| Install libappindicator1
if you get some error for installing libappindicator1 like:
```
E: Package 'libappindicator1' has no installation candidate
```
Package was removed from Kali repositories You will need to manually install the missing packages. First check your CPU architecture, for that run command:
```bash
lscpu | grep Architecture
```

So for my case it's amd64, you can find other versions there too.
[libappindicator1_0.4.92-7_amd64.deb](https://pkgs.org/download/libappindicator1 https://pkgs.org/download/libindicator7).

* now before we jump to install it, need to install libdbusmenu-gtk4 if you don't have it:
```bash
sudo apt --fix-broken install
sudo apt install libdbusmenu-gtk4
```

* then run commands down below:
```bash
curl -p --insecure "http://ftp.de.debian.org/debian/pool/main/liba/libappindicator/libappindicator1_0.4.92-7_amd64.deb" --output libappindicator1_0.4.92-7_amd64.deb
&& curl -p --insecure "http://ftp.de.debian.org/debian/pool/main/libi/libindicator/libindicator7_0.5.0-4_amd64.deb" --output libindicator7_0.5.0-4_amd64.deb
```
* and then change the current working directory to download directory that you downloaded the libappindicator1_0.4.92-7_amd64.deb
and run comm down below:
```bash
dpkg -i libappindicator1_0.4.92-7_amd64.deb
```
* and now you fixed all the errors for installing Discord.
for installing Discord change the current working directory to download directory that you downloaded the deb file of Discord and run the dpkg to install it.
```bash
sudo dpkg -i discord-0.0.17.deb
```
