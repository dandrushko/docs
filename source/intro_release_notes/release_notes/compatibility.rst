
.. _compatibility:

====================
Compatibility Guide
====================

This guide is aimed at OpenNebula 6.8.x users and administrators who want to upgrade to the latest version. The following sections summarize the new features and usage changes that should be taken into account, or are prone to cause confusion. You can check the upgrade process in the :ref:`corresponding section <upgrade>`. If upgrading from previous versions, please make sure you read all the intermediate versions' Compatibility Guides for possible pitfalls.

Visit the :ref:`Features list <features>` and the :ref:`What's New guide <whats_new>` for a comprehensive list of what's new in OpenNebula 7.0.

VM Drivers
================================================================================

We changed default for `CLEANUP_MEMORY_ON_STOP` to `no` as it could potentially lead to heavy workload on hosts when multiple VMs were stopped or migrated in parallel, e.g. when running `onehost flush`.


Ruby gems opennebula and opennebula-cli
================================================================================
Opennebula and opennebula-cli gems both require Nokogiri gem as a running dependency. As nokogiri from 1.16 requires Ruby >= 3.0 we locked Nokogiri to 1.16 to avoid installation failure on systems such as AlmaLinux 8, Debian 10, Ubuntu 20.04. In next 7.0 we will revisit this issue.
