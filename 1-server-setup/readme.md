# Server Setup

Login using ssh

```
ssh root@172.105.60.205
```

Always run the apt update command before apt upgrade to ensure that you have the latest packages available.

```
apt update
apt upgrade
```

Change password (optional)

```
passwd
```

Add non-root user and add it to sudoers

```
usp
groups <username>
usermod -aG sudo <username>
```

Change password for the user

```
sudo passwd username
```

Connect shell with the new user

```
ssh <username>@192.IP.IP.IP
```

Connect to the server using SSH

Generate ssh key from your local machine

```
ssh-keygen -t ed25519 -C "user@gmail.com"
```

to view the public key

```
cat ~/.ssh/id_ed25519.pub
```

Once you have generated the SSH keys, you can add them to your server using the following command

On your server, run the following command to copy the public key to the server. Create a new directory called .ssh in your home directory if it doesn’t already exist. Then create a new file called authorized_keys in the .ssh directory and paste the public key into the file.

```
nano ~/.ssh/authorized_keys
```

if folder does not exist create folder then create file

```
cd ~
mkdir .ssh
nano authorized_keys
```

add it to the ssh utility (run on your local machine)

```
ssh-add -k ~/.ssh/id_ed25519
```

Great, Now you can login without password. 🎉

Disable password login your server

```
sudo nano /etc/ssh/sshd_config

```

Open this file in nano editor and search for PasswordAuthentication and change it to no. Optionally, you can also change the PermitRootLogin to no to prevent root user from logging in.

```
sudo service ssh restart
```

Firewall configuration

```
sudo apt install ufw
```

[Follow the documentation of ufw to enable and disable ports](https://help.ubuntu.com/community/UFW)
