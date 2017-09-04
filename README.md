vmware-harbor
=========

An Ansible(tm) role Installs Harbor(tm) from VMware(tm) as the dependancies from Docker(tm).

* http://vmware.github.io/harbor/

Work in progress. Currently deploys from a local file, tested on CentOS 7

Requirements
------------

If generating certificates, python-pyOpenSSL ( >=16.0.0 ) is needed on the installed host, and Ansible 2.3 (for openssl_privatekey, openssl_publickey)

This is isn't readily available for CentOS 7 and is not in EPEL. Some kind of multi level dependancy hell that makes me think signing a cert on the command line would be easier.


Role Variables
--------------

Some defaults:

Installation sources / parameters:

  harbor_install_tmp: /tmp/harbor
  harbor_install_dir: /tmp/harbor_install
  harbor_install_download: https://github.com/vmware/harbor/releases/download/v1.1.2/harbor-offline-installer-v1.1.2.tgz
  harbor_install_tgz: harbor-installer.tgz
  harbor_install_assume_deps_installed: False
  harbor_install_upload_localcopy_of_installer:  #if set it installs from this address

These end up in harbor.cfg

  harbor_hostname: localhost
  harbor_ui_url_protocol: http
  harbor_db_password: root123
  harbor_customize_crt: on
  harbor_secretkey_path: /data
  harbor_admin_password: Harbor12345
  harbor_auth_mode: db_auth
  harbor_self_registration: on
  harbor_project_creation_restriction: adminonly
  harbor_verify_remote_cert: on

Dependencies
------------

None?

Example Playbook
----------------

Install using a locally hosted copy of the installation tar:

    - hosts: servers
      name: install VMWare Harbor registry
      roles:
        - mkgin.vmware-harbor
      vars:
        - harbor_install_upload_localcopy_of_installer: /tmp/harbor-offline-installer-v1.2.0-rc3.tgz

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
