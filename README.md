# ansible-ssh-config
Ansible role to manage ssh configs.

[![Build Status](https://img.shields.io/travis/feffi/ansible-ssh-config.svg)](https://travis-ci.org/feffi/ansible-ssh-config) [![Github All Releases](https://img.shields.io/github/downloads/feffi/ansible-ssh-config/total.svg)](https://github.com/feffi/ansible-ssh-config) [![GitHub forks](https://img.shields.io/github/forks/feffi/ansible-ssh-config.svg?style=social&label=Fork)](https://github.com/feffi/ansible-ssh-config) [![GitHub stars](https://img.shields.io/github/stars/feffi/ansible-ssh-config.svg?style=social&label=Star)](https://github.com/feffi/ansible-ssh-config) [![GitHub watchers](https://img.shields.io/github/watchers/feffi/ansible-ssh-config.svg?style=social&label=Watch)](https://github.com/feffi/ansible-ssh-config) [![Twitter Follow](https://img.shields.io/twitter/follow/feffi1.svg?style=social&label=Follow)](https://twitter.com/feffi1) [![License](http://img.shields.io/:license-mit-blue.svg)](https://github.com/feffi/ansible-ssh-config/blob/master/LICENSE)

## Role Defaults Variables

```yaml
# Sections and key-value pairs to include in the users .ssh-config
ssh_config:
  # Destination directory of the config file
  destination: "{{ ansible_env.HOME + '/.ssh' }}"

  # Sections and key-value pairs to include in the users .gitconfig
  config:
    - { Host: "localhost 127.0.0.1", Hostname: "127.0.0.1", User: "root" }

secrets:
  ssh:
    # Private ssh key, multiline terminated with \n
    private: ""

    # Public ssh key, multiline terminated with \n
    public: ""
```

Example:

```yaml
- hosts: all
  vars:
    ssh_config:
      config:
        - { Host: "localhost 127.0.0.1", Hostname: "127.0.0.1", User: "root" }
    secrets:
      ssh:
        private: "-----BEGIN RSA PRIVATE KEY-----\n
MIIBOAIBAAJAbO38dp/t36o48N1ydDv5cNe+fL/sEJ1zDFdUetoOv6VP1eqGDNMs\n
8SvhOYR/ry/Lv5ldofonC8P0JckBhNiNJwIDAQABAkAsGIMU+lTvMBdw2hRVHVoy\n
5gNEuOS1LSe/nTKjsNY7mgZZQ83D1f3zgdpBK6fkcPoMda5vNedWx+2uT+2tn1Zx\n
AiEAtzXu/6vbnvcb6yhFj76JaUfiA0n4oBappZ2I5uExRT0CIQCYNQu53yo3Xj6v\n
p7N0LNqpIFpI8mTadQrTGBbEEZbqMwIgUrM+yhw6i9xBtvm7xLIedu6iwBdQ6nqw\n
Y3jkBkwaoIUCIHbgDy13R3CA8fKcxsJ4ebrXoswQTIZ2HSMrUDSIDFcTAiA4BR7m\n
KfKkfU4gSp5KI1WpQMClE3FMneNYrbbsZKdZ3w==\n
-----END RSA PRIVATE KEY-----\n"
        public: "-----BEGIN PUBLIC KEY-----\n
MFswDQYJKoZIhvcNAQEBBQADSgAwRwJAbO38dp/t36o48N1ydDv5cNe+fL/sEJ1z\n
DFdUetoOv6VP1eqGDNMs8SvhOYR/ry/Lv5ldofonC8P0JckBhNiNJwIDAQAB\n
-----END PUBLIC KEY-----\n"
  roles:
    - { role: feffi.ssh-config }
```
