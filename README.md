- ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
- copy private key and public key, set private key as ANSIBLE_PRIVATE_KEY repo secret
- create repo vars ANSIBLE_USER TIMEZONE 

# To run the playbook

```bash
ansible-playbook ./servers.yml -e ansible_user={your remote user}
```

or if you want to run for a particular tag

```bash
ansible-playbook ./servers.yml -e ansible_user={your remote user} -t services
```