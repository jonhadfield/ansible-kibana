kibana
========

Ansible role which installs kibana.

Requirements
------------

Tested on Anbsible 1.6

    Basic auth has been setup for kibana access. 
    read  - user: cheese   password: toast
    write - user: marmite  password: cashews

Role Variables
--------------
    kibana_online_install: true               # Whether or not to perform an online installation by downloading the installer
    kibana_installer_path: /var/installers    # Where to find the installer for an offline installation
    kibana_version: 3.0.1                     # The version of kibana to install
    kibana_base_install_dir: /apps            # Where to install kibana 
    kibana_elasticsearch_url:                 # The url for elasticsearch (accesible to users of Kibana)
    kibana_elasticsearch_cluster_members:     # List of upstream elasticsearch servers (first is primary, the rest are backups)
      - es1:9200
      - es2:9200
      - es3:9200

Dependencies
------------

nginx # Calls 'restart nginx' handler when configuration is created

Example Playbook
-------------------------

    - hosts: all
      sudo: yes
      roles:
         - nginx
         - kibana

License
-------

MIT

Author Information
------------------

Jon Hadfield
