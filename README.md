# ansible-ssh-config
### Provision new virtual servers that are pre-configured with default root and password access
#### The playbook performs several security-related tasks, including disabling the root user and password login for increased protection. It also creates a new user with full sudo access, typically named "admin," and sets up password-based sudo authentication. Additionally, the playbook changes the default SSH port (22) to a different value to enhance security.

### Requirements
 - Ansible (tested on version 2.8.1)
 - Root's password to destination server
 - Server's distro must support sudo command.
 - sshpass utility.
## Generate private and public keys

```bash
ssh-keygen -t rsa -b 4096 -m PEM -f keyname
```

Replace `keyname` with your name (e. g. `myserver`). Enter passphrase if you want to (or skip this step).

This command will create two files: private key (without extension) and public key (ends with `.pub`).

## Run a command

1. Download the playbook.

```bash
wget https://raw.githubusercontent.com/s-mokrushin/ansible-ssh-setup/master/setup-ssh.yml -O setup-ssh.yml
```

2. Prepare the command with your arguments.

```bash
ansible-playbook \
    setup-ssh.yml -i 123.123.123.123, \
    -u root \
    --become \
    --ask-pass \
    --extra-vars "admin_username=admin admin_password=verysecretpassword public_key_path=/path/to/keyname.pub ssh_port=22222"
```

* Change IP `123.123.123.123` to your server's IP address (keep character "`,`").
* Replace `admin_user` value with your name (if needed).
* Replace `admin_password` value with your password (use a strong password). This password used for `sudo` command.
* Replace `public_key_path` value with your public key path.
* Replace `ssh_port` value with any other allowed number (due to security reasons).

3. Run the command. Enter `root`'s password.
