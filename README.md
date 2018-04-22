## Ansible Sample

Sample ansible scripts for Azure

### Preparation

Install [ansible](https://www.ansible.com/). If you're using password instead of sshkey you need to install `sshpass` too.

```
sudo apt install -y ansible
sudo apt install -y sshpass
```

### Pingtest

Ping test inventory

- update/add host then run command

```
ansible -i hosts all -m ping -u <user>
```

For non-sshkey, ping test inventory

- update *username* and *password* in `hosts.pass` then run command

```
ansible -i hosts.pass all -m ping 
```

### Simple

Install nginx+php on webserver

```
ansible-playbook -i hosts site.yaml
```

### Ntier

N-tier Web/App ansible sample to install/config nginx+ssl on webserver and nginx+php on appserver

- update hosts of webserver and appservers
- add your certificate (`cert.pem` & `key.pem`) files in `roles/web/files`

```
ansible-playbook -i hosts site.yaml
```

To get a free certificate, please visit [letsencrtyp](https://letsencrypt.org/)

## Reference

Overview: https://www.slideshare.net/deview/1a7ansible?qid=14b75cf7-b2bc-4596-84eb-3b3c53355161

Examples: https://github.com/ansible/ansible-examples

Best Practice: https://www.youtube.com/watch?v=5BhAJ4mEfZ8&t=2778s

