# ansible-certupdate-nginx
Ansible role to copy certificates to a specific folder (created as needed)

NOTE: this is stll a skeleton; things will be updated *real soon now*.

## Background
I needed to break up a rather monolithic playbook for setting up Jenkins on a VM; part of it involved getting SSL setup for nginx. I later realized the certupdate piece would be needed on another host responsible for auto-renewing certificates. This is one of several such roles involved.

### Prep
Though it wasn't as obvious as I'd hoped, the following command is needed to create the correct role structure or any attempt to install it using galaxy later will fail in spite of a correctly formatted `requirements.yml` in the repo base. The command involved (plus output) turned out to be:
```
$ ansible-galaxy role init --offline -vvvv --init-path ansible-certupdate-nginx certupdate_nginx
ansible-galaxy 2.9.6
  config file = /home/zeromaster/.ansible.cfg
  configured module search path = ['/home/zeromaster/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python3/dist-packages/ansible
  executable location = /usr/bin/ansible-galaxy
  python version = 3.8.10 (default, Jun  2 2021, 10:49:15) [GCC 9.4.0]
Using /home/zeromaster/.ansible.cfg as config file
- Role certupdate_nginx was created successfully
```
Using `--offline` foregoes trying to create a role in the official Galaxy directory, along with the use of API keys and such.

The `certupdate_nginx/meta/main.yml` file then needs to be fleshed out to at least a minimum level. At that point the working tasks and other sundries can be populated in the repo and re-used, assuming things are reasonably thought out.
