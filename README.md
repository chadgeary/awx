# Reference
Ansible playbook to install AWX (pulled via git) then installed with an Apache HTTP proxy using auto-renewed Let's Encrypt web certificate.

# Auth
Admin's generated password is located in /opt/awx/awx_credential

# Requires
- CentOS 7 or Ubuntu 18.04/20.04

# Requires for Lets Encrypt
- Valid domain name ( it should NOT match the server's hostname, to properly redirect the HTTPS proxy )
- Server's 80/tcp globally reachable 

# Variables
```
# web_port, the local port for awx to listen on, e.g.:
8002

# target
the server targeted for the awx installation
```

# Optional variables (Lets Encrypt SSL)
```
# le_enable, the flag to use Lets Encrypt
True

# certbot_contact_email, required for certbot e.g.:
chad@chadg.net

# friendly_name, a valid domain name for registering lets encrypt web certificate e.g.:
awx.chadg.net
```

# Example
```
# Local deployment with LetsEncrypt
ansible-playbook awx.yml --extra-vars '{"le_enable":True,"certbot_contact_email":"chad@chadg.net","friendly_name":"awx.chadg.net","web_port":"8002","target":"localhost"}'

# Local deployment without LetsEncrypt
ansible-playbook awx.yml --extra-vars '{"le_enable":False,"web_port":"8002","target":"localhost"}'
```
