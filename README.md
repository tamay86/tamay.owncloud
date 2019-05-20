Ansible Role: tamay.owncloud
=========

This role installs the community edition of [ownCloud](https://owncloud.org/).

This role will only download and configure ownCloud. The [requirements](https://doc.owncloud.org/server/10.1/admin_manual/installation/system_requirements.html) have to be met.

Requirements
------------

- Database Server
- Webserver with PHP

Role Variables
--------------

List of all variables, including default values.

    # Version of owncloud to download
    # Example: '10.0.1', '10.1.1' or '10.2.0'
    owncloud_version: '10.2.0'

The ownCloud version that should be installed. Visit the [downloads page](https://owncloud.org/download/#owncloud-server-tar-ball) to view the latest version.  
    
    # Document root of owncloud
    owncloud_dir: /var/www/owncloud

The directory, where the ownCloud will be extracted to. 
    
    # Data directory of owncloud
    owncloud_data_dir: "{{ owncloud_dir }}/data"

The directory, that holds the user data.
    
    # User and group for owncloud_dir
    owncloud_user: apache
    owncloud_group: apache

Unix file permissions for the ownCloud folder. Usually it's the webserver user.
    
    # Database settings
    owncloud_database: mysql
    owncloud_database_name: owncloud
    owncloud_database_host: localhost
    owncloud_database_user: owncloud
    owncloud_database_pass: password
    owncloud_database_table_prefix: oc_

Configuration to connect to the database.
    
    # Admin user settings
    owncloud_admin_user: admin
    owncloud_admin_pass: admin

The initial administrative user and his password.
    
    # URL for owncloud
    owncloud_url: "{{ ansible_fqdn }}"

The URL of your ownCloud installation.
    
    # Installs or removes marketplace apps
    owncloud_apps:
      enabled: []
      disabled: []
    # Example:
    #owncloud_apps:
    #  enabled:
    #    - brute_force_protection
    #    - calendar
    #    - contacts
    #    - files_pdfviewer
    #    - files_texteditor
    #    - tasks
    #  disabled:
    #    - external

Every app in ```enabled``` will be installed and enabled.
Every app in ```disabled``` will only be disabled, but not removed.
For a list of possible values execute ```./occ market:list```

Dependencies
------------

None.

Example Playbook
----------------

For a complete playbook to install ownCloud with MariaDB, httpd, and php, see ```tests/test.yml```


License
-------

MIT

Author Information
------------------

tamay.mueller@gmail.com
