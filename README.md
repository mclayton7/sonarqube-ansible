# sonarqube
This set of [Ansible](https://www.ansible.com/) playbooks is used for deploying and upgrading a SonarQube instance on a CentOS 7 machine.

## Setup
Run the ansible playbook from the ```playbooks``` directory with the following command, replacing ```<username>``` with a user account on the remote system:
```
ansible-playbook --become-user <username> --ask-pass -Ki inventory main.yml
```

## Notes
SonarQube comes with an Administrator account with the following credentials ```admin```/```admin```. Be sure to remove/disable this account once the server is setup.


## SSL Certificate
The nginx configuration requires a `.pem` and a `.key` for https/TLS encryption

Generating the `.pem` bundle:
```bash
openssl pkcs12 -nokeys -in server-cert-key-bundle.p12 -out server-ca-cert-bundle.pem
```

Generating the server `.key` file:
```bash
openssl pkcs12 -nocerts -nodes -in server-cert-key-bundle.p12 -out server.key
```

http://ehealth-aussie.blogspot.com/2013/06/convert-p12-bundle-to-server.html