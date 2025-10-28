# ansible shorts

## What to do to start with simple settings for ansible.

assumes to run with a user to become root.
```
visudo
``` 
my-user-for-ansible-to-use ALL=(ALL) NOPASSWD: ALL

```
sudo usermod -aG wheel my-user-for-ansible-to-use
```
Best would be restart to have no problem become root with my-user-for-ansible-to-use and ansible.

### change yamllint-rename-to-dot-file

```
mv yamllint-rename-to-dot-file .yamllint
```
### create a id_ed25519 ssh-keyfile

```
ssh-keygen -t ed25519 -C "your_email@example.com"
```

The id_ed25519.pub must be allowed on the remote machine in the ~/.ssh/authorized_keys file.
settings must be 600 for the file

```
chmod 600 ~/.ssh/authorized_keys
```

### change settings in hosts.ini


[mainserver]\
127.0.0.1

[multi:children]\
mainserver

ansible_ssh_user=my-user-for-ansible-to-use\
ansible_ssh_private_key_file=~/.ssh/id_ed25519


### annsible.cfg 

remote_tmp=/tmp could be changed if needed with jailed systems 

### install-package.txt
How to install a package.

```
ansible -i hosts.ini multi  -b -m package -a "name=chrony state=present"
```

### install-logrotate.yml

Installs and checks settings for logrotate.

```
ansible-playbook activate-logrotate-cronjob.yml -i hosts.ini
```
### activate-logrotate-cronjob.yml

aktivates a cronjob with settings set to file on remote host.

script is echo-hello.sh

check with crontab -l with root use.Better use other user.

### sysctl-swapiness.yml

sets swapiness to 1, change sysctl_value: "1" if needed.

```
ansible-playbook sysctl-swapiness.yml -i hosts.ini
```

### upgrade.yml

Upgrade a RHEL system with dnf.

```
ansible-playbook upgrade.yml -i hosts.ini
```

### Interresting things for RHEL Systems

See https://dnf.readthedocs.org/en/latest/automatic.html


