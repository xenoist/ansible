# ansible shorts

What to do to start with simple settings for ansible.

## change yamllint-rename-to-dot-file

***
mv yamllint-rename-to-dot-file .yamllint
***

## change settings in hosts.ini

***
[mainserver]
127.0.0.1

[multi:children]
mainserver

ansible_ssh_user=my-user-for-ansibleto-use
ansible_ssh_private_key_file=~/.ssh/id_ed25519-remote
***

## ainsible.cfg 

remote_tmp=/tmp could be changed if needed with jailed systems 

## Interresting things for RHEL Systems

See https://dnf.readthedocs.org/en/latest/automatic.html


