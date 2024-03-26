
.. _compatibility:

====================
Compatibility Guide
====================

This guide is aimed at OpenNebula 6.8.x users and administrators who want to upgrade to the latest version. The following sections summarize the new features and usage changes that should be taken into account, or are prone to cause confusion. You can check the upgrade process in the :ref:`corresponding section <upgrade>`. If upgrading from previous versions, please make sure you read all the intermediate versions' Compatibility Guides for possible pitfalls.

Visit the :ref:`Features list <features>` and the :ref:`What's New guide <whats_new>` for a comprehensive list of what's new in OpenNebula 7.0.

VM Drivers
================================================================================

We changed default for `CLEANUP_MEMORY_ON_STOP` to `no` as it could potentially lead to heavy workload on hosts when multiple VMs were stopped or migrated in parallel, e.g. when running `onehost flush`.
