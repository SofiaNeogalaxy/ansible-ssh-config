# ansible-ssh-config
### Provision new virtual servers that are pre-configured with default root and password access
#### The playbook performs several security-related tasks, including disabling the root user and password login for increased protection. It also creates a new user with full sudo access, typically named "admin," and sets up password-based sudo authentication. Additionally, the playbook changes the default SSH port (22) to a different value to enhance security.

### Requirements
 - Ansible (tested on version 2.8.1)
 - Root's password to destination server
 - Server's distro must support sudo command.
 - sshpass utility.
