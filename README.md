Evergreen Playbook
==================

Install Evergreen on a standalone server.

QuickStart
----------

Install VirtualBox, Vagrant, Ansible and clone the Evergreen Playbook. From the Playbook directory:

  $ vagrant up --no-provision
  $ # ssh into the machine and run 'cpan' for root (use sudo for modules)
  $ vagrant provision

After the provisioning process has completed you should have a working Evergreen install (on a VM using 4GB ram).

- The public interface (opac) will be viewable at: http://localhost:3001
- SSL: https://localhost:4443
- The staff client can be downloaded from: http://localhost:3001/updates/manualupdate.html

However, to get rid of those port numbers, quick and dirty for OSX:

  $ sudo ipfw add 100 fwd 127.0.0.1,3001 tcp from any to me 80
  $ sudo ipfw add 101 fwd 127.0.0.1,4443 tcp from any to me 443

You should now be able to use http://localhost and https://localhost.

Using without Vagrant
---------------------

Easy:

- Create a hosts file similar to vagrant pointing at the appropriate server(s)
- Create a site.yml file similar to vagrant.yml specifying the roles for the server(s)
- Use standard Ansible commands: ansible-playbook -i hosts -K site.yml

Configuration
-------------

Default variables are in the group_vars folder. Adjust to suit, add host_vars if needed.

For the future
--------------

- Postgres specific role
- Build in support for Evergreen versions
- Version the template files
- Add SipServer

Issues
------

- Only tested with Ubuntu 12.04 LTS (precise) and OpenSRF / Evergreen master.
- For errors related to creating the jabber users (other than already registered) up the sleep time.

License & Authors
-----------------
- Author:: Mark Cooper (<mark.c.cooper@outlook.com>)

GPL v3
