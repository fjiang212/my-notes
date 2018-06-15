# Installation
* http://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html

# Commands
* Playbook
```
ansible-playbook -i hosts-local example.yml --ask-vault-pass -u vagrant--extra-vars "env=development application=abc"
ansible-playbook -i hosts example.yml --extra-vars '{"env":"development", "application":"abc", "servers": ["10.0.2.15:5045"]}'
```
# Examples
* https://galaxy.ansible.com
* https://github.com/elastic/ansible-elasticsearch

