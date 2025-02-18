# Preliminary utilities

In this section I will list the utilities I install on a fresh Linux system. This is not a complete list, but rather a list of the utilities I will assume as available in the rest of the documentation.

```bash
sudo apt update && sudo apt -y upgrade
sudo apt -y install curl git cmake clang libssl-dev mold net-tools openssh-server htop libpq-dev libfuse2 libfontconfig-dev
```

## Additional repositories

```bash
sudo add-apt-repository ppa:atareao/telegram -y
sudo apt install software-properties-common apt-transport-https curl -y
```

```bash
curl -fSsL https://updates.signal.org/desktop/apt/keys.asc | gpg --dearmor | sudo tee /usr/share/keyrings/signal-desktop-keyring.gpg
```

```bash
echo deb [arch=amd64 signed-by=/usr/share/keyrings/signal-desktop-keyring.gpg] https://updates.signal.org/desktop/apt xenial main | sudo tee /etc/apt/sources.list.d/signal-messenger.list
```

Before installing software from the repository, you should update the package list:

```bash
sudo apt update
```

## Software

```bash
sudo apt -y install telegram signal-desktop
```

## Firewall ports

```bash
sudo ufw allow ssh
```
