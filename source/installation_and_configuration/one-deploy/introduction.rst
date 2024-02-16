.. _ignc:
.. _one-deploy:

================================================================================
About one-deploy
================================================================================

`one-deploy` is a set of Ansible playbooks that automate the deployment of OpenNebula, allowing complex configurations to be done in a few steps.

Some of the features it provides are :

- Installation and configuration of OpenNebula
- Virtual network definitions
- HA (multiple frontend) installation
- Ceph hiperconverged deployments
- Installation through a Bastion (access node to a private net)

================================================================================
Dependencies 
================================================================================

In order to use `one-deploy`, the following software is needed to be configured in the computer that will run

- An ``ssh`` client, to connect to the servers that will run OpenNebula
- ``git``, to download the necessary playbooks
- ``ansible`` version >= 6 (core > 2.0)
- ``make``, to run the playbooks in an easier way 
- A text editor, preferably with YAML syntax highlighting

.. note::

  It is not the objective of this document to explain how Ansible must be installed. The documentation about how to install it in certain Linux Distributions can be found in https://docs.ansible.com/ansible/latest/installation_guide/installation_distros.html

================================================================================
Downloading and preparing one-deploy
================================================================================

The playbooks can be cloned from the following git repository

.. prompt:: bash # auto
  $ git clone --recursive https://github.com/OpenNebula/one-deploy.git

Once the clone is finished, some extra requirements must be installed with the following command

.. prompt:: bash # auto
  $ make requirements

.. note::

  After this moment, there are two different ways to invoke ``ansible``: directly or using ``make``. Both of them will be described


