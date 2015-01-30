kibana
========

Ansible role which installs kibana.

Requirements
------------

Tested on Anbsible 1.6

Role Variables
--------------
    kibana_online_install: true                        # Whether or not to perform an online installation by downloading the installer
    kibana_installer_path: /tmp/kibana-3.0.1.tar.gz    # Where to find the installer for an offline installation
    kibana_version: 3.0.1                              # The version of kibana to install
    kibana_base_install_dir: /apps                     # Where to install kibana 
    kibana_elasticsearch_url: https://example/com/es   # The url for elasticsearch (accesible to users of Kibana)
    kibana_elasticsearch_cluster_members:              # List of upstream elasticsearch servers (first is primary, the rest are backups)
      - es1:9200
      - es2:9200
      - es3:9200
    kibana_healthcheck_url: /check                     # Expected healthcheck request
    kibana_healthcheck_file: /check.html               # File to return as response to healthcheck
    kibana_healthcheck_content: OK                     # Content of http response
    kibana_htpasswd_files_path:                        # Where to find kibana.htpasswd and kibana-write.htpasswd
    kibana_purge_htpasswd: false                       # Delete htpasswd files 
    kibana_read_users:                                 # List of user hashes with read access (Requires python-passlib)
      guest:
        username: guest
        password: password
    kibana_write_users:                                # List of user hashes with write access (Requires python-passlib)
      first_last:
        username: lastf
        password: secret
    kibana_admin_users:
      first_last:
        username: admin_username
        password: more_secret

Dependencies
------------

nginx # Calls 'restart nginx' handler when configuration is created or modified

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
