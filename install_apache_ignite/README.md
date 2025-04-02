install_apache_ignite
=========

This is a simple role to deploy Apache Ignite on your servers.


## Requirements

Used only ansible.builtin modules

## Role Variables

### vars/main.yml

**Make the necessary changes to this file to get the required configuration to deploy Ignite on your servers.**

`ignite_version` - desired Apache Ignite version to download and install
```
ignite_version: "2.17.0"
```
`ignite_dir:` - path to install Ignite on server nodes. By default, is equal to "/opt/ignite".

Your owner and group for creating dirs. You can set these variables in vars/main.yml (will be used for all servers).
```
ignite_owner: <your_owner>
ignite_group: <your_group>
```
Or you can set different owner and group for each server in your inventory. For example:
```
[my_server]
my_srv1 ansible_host=<IP or FQDN> ansible_user=<login> ignite_owner=ignite  ignite_group=ignite
```
`ignite_delete_logs_before_install:` - set **True** if you want to delete logs dir before install

`ignite_persistence_enabled:` - set **"true"** if you need configuration with persistence default data region.

`ignite_create_test_cache:` - set **True** if you need to create test cache in server nodes configuration. See in customIgniteConfiguration.xml.j2 

`ignite_use_calcite:` - set **True** if you want to use the Calcite SQL engine in Ignite. Otherwise, the default H2 engine will be used.

`ignite_use_rest:` - set **True** if you want to use http REST in Ignite

`ignite_print_metrics_in_log:` - set **False** if you don't need to print metrics into log file for reducing size. Equals to metricsLogFrequency=0

`ignite_run_as_service:` set **True** if you want to run Ignite as systemd service (ignite-server.service by default)

`ignite_start_after_install:` set the value to **True** if you need to automatically launch Ignite immediately after installation.


### defaults/main.yml

Default values for all other settings



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

