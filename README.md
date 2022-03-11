Ansible Role: Security
=========
This ansible role applies sudoers and ssh security configurations.
Sudoers are managed via a custom sudoer files under */etc/sudoers.d/myuser*.
Sudoer and ssh configs are validated before a permanent update, so it's safe
to change the templates.

**Handle with care as it's easy to lock yourself out and consider logging
into the server when running this role the first time.**

Requirements
------------
None

Variables
------------
SSH port. Make sure you configured your firewall to allow connections to that
port to prevent locking yourself out:
```
security_ssh_port: 22
```

Disable root login:
```
security_permit_root_login: "no"
```

Disable password authentication:
```
security_password_authentication: "no"
```

Disallow empty passwords:
```
security_permit_empty_password: "no"
```

Add users to sudoers with NOPASSWD enabled:
```
security_sudoers_nopasswd: []
```

Add users to sudoers with NOPASSWD disabled:
```
security_sudoers_with_password: []
```

Example Playbook
------------
```
- hosts: all
  vars:
    security_ssh_port: 2888
    security_permit_root_login: yes
    security_sudoers_nopasswd: [ ansible ]
  roles:
    - jamslinger.security
```

License
------------
MIT
