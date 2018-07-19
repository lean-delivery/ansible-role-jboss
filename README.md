ansible-role-jboss
=========

## Summary

This role installs JBoss Application on Linux and Windows platforms
Current JBoss role can be installed to OS Linux 6.* and 7.*. 


Role tasks
------------

 - Create Jboss user (Linux)
 - Install Jboss
   - Additional opportunity to install from s3, web, jboss-org, local source.
 - Set JBOSS_HOME variable (Linux)


Requirements
------------

 - Minimal Version of the ansible for installation: 2.4
 - **Supported jboss versions**:
   - 6
   - 7
 - **Supported OS**:
   - CentOS
     - 6
     - 7
   - Windows:
     - 10


## Role Variables
--------------

  - `jboss_user` - user for jboss
  - `jboss_group` - groupd for jboss user

  - `transport` - artifact source transport
     Available:
      - `jboss-org` - download artifact from http://download.jboss.org with specified:
          - `jboss_major_version`
          - `jboss_minor_version`
          - `jboss_patch_version`
      - `web` - fetch artifact from custom web uri
      - `local` - local artifact

  - `jboss_path` - where jboss should be installed
    default: `/opt/jboss`

  - `download_path` - local folder for downloading artifacts
    default: `/tmp/`

  - `transport_web` - URI for http/https artifact  e.g. "http://my-storage.example.com/jboss-as-7.1.1.Final.zip"
  - `transport_local` - path for local artifact e.g. "/tmp/jboss-as-7.1.1.Final.zip"


Example Playbook
----------------

### Installing Jboss from jboss.org:
```yaml
- name: "Install Jboss from jboss.org"
  hosts: all

  roles:
    - role: "lean-delivery.ansible-role-jboss"
      jboss_major_version: 7
      jboss_minor_version: 1
      jboss_patch_version: 1
```

### Installing Jboss from local file:
```yaml
- name: "Install Jboss from local"
  hosts: all

  roles:
    - role: "lean-delivery.ansible-role-jboss"
      transport: "local"
      transport_local: "/tmp/jboss-as-7.1.1.Final.zip"
```


## License

Apache2

## Authors

authors:
  - Anastacia Maletskaya <anastacia_maletskaya@lean-delivery.com>
