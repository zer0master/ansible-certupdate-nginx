Role Name
=========

This role updates certificates in a custom ssl directory for `nginx`. It was written with LetsEncrypt in mind, but the certificate names and locations may be customized, per the rules of ansible variable precedence.

Requirements
------------

None.

Role Variables
--------------

Values you can override:
* `certs_local_folder`: where your local certs are kept
* `certs_target_folder`: where results will live; your nginx site config must point to them
* `cert_info`: dictionary of names and quoted (octal) modes

Dependencies
------------

Your playbook's list of roles will need to reflect your choice of name of course.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:
```
    - hosts: servers
      roles:
         - role: certupdate_nginx
         - certs_local_prefix: (your role's files/certs location; one or more fqdn-named subfolders will live there)
         - certs_target_folder: (remote certs folder)
         # cert_info: (dict with name/mode info if overriding LetsEncrypt/nginx conventions)
```
License
-------

GNU 2.0

Author Information
------------------

No comment.

Installation
------------

As part of a larger playbook, add the following in `requirements.yml` (`name` can be whatever you prefer):
```
- name: certupdate_nginx
  src: git+https://github.com/zer0master/ansible-certupdate-nginx.git
  scm: git
```
Then install with
```
ansible-galaxy role install -vvvv --role-file requirements.yml --roles-path roles/
```
This assumes a layout with roles, host/group_vars, and possibly inventory as first-level folders.
