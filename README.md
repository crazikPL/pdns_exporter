Role Name
=========

Install Prometheus PowerDNS_Exporter from github repository

Requirements
------------

find and put tarball in your local dir, ie:
```
files/powerdns_exporter-0.1.2.linux-amd64.tar.gz
```

Role Variables
--------------

all variables are defined in defaults:

```yaml
---
# defaults file for pdns_exporter

prometheus_user: prometheus
prometheus_group: prometheus
prometheus_install_path: '/opt/prometheus'
prometheus_config_path: '/etc/prometheus'
prometheus_pid_path: '/var/run/prometheus'
prometheus_loglevel: 'info'

prometheus_pdns_exporter_install_path: '{{ prometheus_install_path }}'
prometheus_pdns_exporter_config_path: '{{ prometheus_config_path }}'
prometheus_pdns_exporter_pid_path: '{{ prometheus_pid_path }}'
prometheus_pdns_exporter_user: '{{ prometheus_user }}'
prometheus_pdns_exporter_group: '{{ prometheus_group }}'
prometheus_pdns_exporter_loglevel: '{{ prometheus_loglevel }}'
prometheus_pdns_exporter_weblisten: '{{ prometheus_pdns_exporter_listen_ip }}:{{ prometheus_pdns_exporter_listen_port }}'
prometheus_pdns_exporter_listen_port: '9120'
prometheus_pdns_exporter_listen_ip: ''
prometheus_pdns_exporter_version: '0.1.2'
prometheus_pdns_exporter_apiurl: "http://localhost:8001/"
prometheus_pdns_exporter_apikey: ''
prometheus_pdns_exporter_metricpath: '/metrics'

enable_ufw: false
prometheus_pdns_exporter_src_access:
  - "{{ ansible_default_ipv4.network }}/{{ ansible_default_ipv4.netmask }}"
```

For typical deployment you can eventually define enable ufw fw and define src access list
Based on defined variables you can set variables common for all prometheus stack

Dependencies
------------

If you want to set fw, you need to have ufw role

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
    - hosts: servers
      roles:
         - { role: pdns_exporter, prometheus_pdns_exporter_apikey: 'XXX' }
```

License
-------

BSD

Author Information
------------------

Tomasz Baczynski
