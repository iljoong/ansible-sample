## Ansible Sample

Sample ansible scripts for Azure

### Preparation

Install [ansible](https://www.ansible.com/). If you're using password instead of sshkey you need to install `sshpass` too.

```
sudo apt install -y ansible
sudo apt install -y sshpass
```

Add all hosts fingerprint to `known_hosts` file by `ssh` to each host.

### Pingtest

Ping test inventory, using sshkey authentication

- update *hosts* in `hosts` and run command

```
ansible -i hosts all -m ping -u <user>
```

For non-sshkey authentication, ping test inventory

- update *hosts*, *ansible_ssh_user* and *ansible_ssh_pass* variables in `hosts.pass`, and run command

```
ansible -i hosts.pass all -m ping 
```

### Simple

Install nginx+php on webserver

- update *hosts* in `hosts`
- update *ansible_ssh_user* and *ansible_ssh_pass* variables in `site.yaml` for non-sshkey authentication
- run command

```
ansible-playbook -i hosts site.yaml
```

### Ntier

N-tier Web/App ansible sample to install/config nginx+ssl on webserver and nginx+php on appserver

- update *hosts* in `hosts` for webservers and appservers
- update *ansible_ssh_user* and *ansible_ssh_pass* variables in `group_vars/all`
- update *app_lb_ip* in `group_vars/all`
- copy your certificate (`cert.pem` & `key.pem`) files in `roles/web/files`

```
ansible-playbook -i hosts site.yaml
```

This sample assumes you have a Ntier environment. To setup the enviroment, please refer [terraform sample](https://github.com/iljoong/azure-terraform).

You also need a certificate to perform this sample and to get a free certificate, please visit [letsencrtyp](https://letsencrypt.org/).

## Reference

Overview: https://www.slideshare.net/deview/1a7ansible?qid=14b75cf7-b2bc-4596-84eb-3b3c53355161

Examples: https://github.com/ansible/ansible-examples

Best Practice: https://www.youtube.com/watch?v=5BhAJ4mEfZ8&t=2778s

