install_apache_ignite
=========

This is a simple role for Apache Ignite deployment on your servers.


Requirements
------------

Used only ansible.builtin modules

Role Variables
--------------

# vars/main.yml

ignite_version - desired Apache Ignite version to download and install
```
ignite_version: "2.16.0"
```
Your owner and group for creating dirs. You can set these variables in vars/main.yml (will be used for all servers).
Or you can set different owner and group for each server in your inventory.
```
ignite_owner: <your_owner>
ignite_group: <your_group>
```

ignite_delete_logs_before_install - Set in True if you want to delete logs dir before install

ignite_persistence_enabled - "true" if you need configuration with persistence default data region.
ignite_create_test_cache - True if you need to create test cache in server nodes configuration. See in customIgniteConfiguration.xml.j2 

ignite_use_calcite: - True if you want to use Calcite SQL engine in Ignite
ignite_use_rest: - True if you want to use http REST in Ignite

Default path to install:
ignite_dir: "/opt/ignite"


Example Playbook
----------------

```
---
- name: Install Apache Ignite
  hosts: <your hosts here>

  roles:
    - install_apache_ignite
```

License
-------

BSD

