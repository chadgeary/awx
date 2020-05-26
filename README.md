# Reference
Ansible playbook to install AWX (pulled via git) then installed with an Apache HTTP proxy using auto-renewed Let's Encrypt web certificate.

# Auth
Admin's generated password is located in /opt/awx_credential

# Requires
- CentOS 7 or Ubuntu 18.04/20.04
- Valid domain name ( it should NOT match the server's hostname, to properly redirect the HTTPS proxy )
- Server's 80/tcp globally reachable (for Let's Encrypt)

# Variables
```
# certbot_contact_email, required for certbot e.g.:
chad@chadg.net

# friendly_name, a valid domain name for registering lets encrypt web certificate e.g.:
awx.chadg.net

# target
the server targeted for the awx installation
```

# Example
```
ansible-playbook -i ~/inventory ansible-awx.yml --extra-vars '{"certbot_contact_email":"chad@chadg.net","friendly_name":"awx.chadg.net","target":"localhost"}'
```
