# ansible shorts

## What to do to start with simple settings for ansible.

### change yamllint-rename-to-dot-file

```
mv yamllint-rename-to-dot-file .yamllint
```

### change settings in hosts.ini


[mainserver]\
127.0.0.1

[multi:children]\
mainserver

ansible_ssh_user=my-user-for-ansibleto-use\
ansible_ssh_private_key_file=~/.ssh/id_ed25519-remote


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

sets swapiness to 1, change if needed

```
ansible-playbook sysctl-swapiness.yml -i hosts.ini
```

### Interresting things for RHEL Systems

See https://dnf.readthedocs.org/en/latest/automatic.html


