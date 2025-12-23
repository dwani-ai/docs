Proton Setup

- Website
    - https://protonvpn.com/support/official-linux-vpn-ubuntu

```bash
wget https://repo.protonvpn.com/debian/dists/stable/main/binary-all/protonvpn-stable-release_1.0.8_all.deb


sudo dpkg -i ./protonvpn-stable-release_1.0.8_all.deb && sudo apt update

sudo apt install proton-vpn-gnome-desktop

sudo apt install libayatana-appindicator3-1 gir1.2-ayatanaappindicator3-0.1 gnome-shell-extension-appindicator
```


--- Uninstall

```bash
sudo apt autoremove proton-vpn-gnome-desktop && sudo apt purge protonvpn-stable-release
```