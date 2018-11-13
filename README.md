# ansible-ssh-config

Ansible role to manage ssh configs.

[![Build Status](https://img.shields.io/travis/feffi/ansible-ssh-config.svg)](https://travis-ci.org/feffi/ansible-ssh-config) [![Github All Releases](https://img.shields.io/github/downloads/feffi/ansible-ssh-config/total.svg)](https://github.com/feffi/ansible-ssh-config) [![GitHub forks](https://img.shields.io/github/forks/feffi/ansible-ssh-config.svg?style=social&label=Fork)](https://github.com/feffi/ansible-ssh-config) [![GitHub stars](https://img.shields.io/github/stars/feffi/ansible-ssh-config.svg?style=social&label=Star)](https://github.com/feffi/ansible-ssh-config) [![GitHub watchers](https://img.shields.io/github/watchers/feffi/ansible-ssh-config.svg?style=social&label=Watch)](https://github.com/feffi/ansible-ssh-config) [![Twitter Follow](https://img.shields.io/twitter/follow/feffi1.svg?style=social&label=Follow)](https://twitter.com/feffi1) [![License](http://img.shields.io/:license-mit-blue.svg)](https://github.com/feffi/ansible-ssh-config/blob/master/LICENSE)

## Role Defaults Variables

```yaml
# Sections and key-value pairs to include in the users .ssh-config
ssh_config:
  # The owner of the keys
  owner: {
    name: "feffi",
    group: "feffi"
  },
  # Destination directory of the config file
  destination: "{{ ansible_env.HOME + '/.ssh' }}"
  # SSH key pairs to publish
  keys: [
    {
        # The filename prefix of the key
        prefix: "id",
        # Private ssh key, multiline terminated with \n
        private: "...",
        # Public ssh key, multiline terminated with \n
        public: "..."
      }
  ]
  # Sections and key-value pairs to include in the users .gitconfig
  config:
    - { Host: "localhost 127.0.0.1", Hostname: "127.0.0.1", User: "root" }
```

Example:

```yaml
- hosts: all
  vars:
    ssh_config:
      # The owner of the keys
      owner:
        name: "feffi"
        group: "feffi"
      config:
        - { Host: "localhost 127.0.0.1", Hostname: "127.0.0.1", User: "root" }
    secrets:
      ssh:
        private: "..."
        public: "..."
  roles:
    - { role: ansible-ssh-config }
```
