================================================================================
Hosts preparation
================================================================================

Before running the playbook be sure that all the servers are accessible via ssh (or can be accessed 'jumping' with the bastion). Some good practices here would be

- Do not use root user to deploy OpenNebula in the servers. Better create a new user in all the servers and add a ``sudoers`` entry to allow it to become root. 
- Ansible allows the definition of passwords for the user and for becoming root, but it is better to setup the ``authorized_hosts`` in all the servers.
- Having DNS resolution for all the servers (or entries for them in the ``/etc/hosts`` file of the execution machine, the bastion and all the servers) will simplify the inventory file.


