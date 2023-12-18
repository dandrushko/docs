.. _kvm_contextualization:

================================================================================
Open Cloud Contextualization
================================================================================

Option 1: Prepare the Virtual Machine Image using Packer
================================================================================

Checkout one-apps repository

.. prompt:: bash $ auto

    $ git clone git@github.com:OpenNebula/one-apps.git

Ensure you have all the `requirements <https://github.com/OpenNebula/one-apps?tab=readme-ov-file#requirements>`__
and build some of the supported images using make

.. code-block:: bash

    Usage examples:
        make <distro>          -- build just one distro
        make <service>         -- build just one service

        make all               -- build all distros and services
        make all -j 4          -- build all in 4 parallel tasks
        make distros           -- build all distros
        make services          -- build all services

        make context-linux     -- build context linux packages
        make context-windows   -- build windows linux packages

    Available distros:
        alma8 alma9 alpine316 alpine317 alpine318 alt9 alt10 amazon2
        centos7 centos8stream debian10 debian11 debian12 devuan3 devuan4
        fedora37 fedora38 freebsd12 freebsd13 ol8 ol9 opensuse15 rocky8
        rocky9 ubuntu2004 ubuntu2004min ubuntu2204 ubuntu2204min

    Available services:
        service_vnf service_wordpress service_OneKE

Structure of the repository is following

.. code-block:: bash

    .
    ├── appliances          # src for "service appliances"
    │   ├── lib             # WordPress, VNF and OneKE
    │   ├── OneKE
    │   ...
    │
    ├── build               # target directory with built images
    │
    ├── context-linux       # src for linux context pacakges
    │
    ├── context-windows     # src for windows context pacakges
    │
    ├── Makefile            # for Packer orchestration
    ├── Makefile.config
    │
    └── packer              # for each distro:
        ├── alma            #   - packer template
        ├── alpine          #   - customization scripts (*.sh)
        ...                 #   - cloud-init.yaml userdata (if needed)
        └── ubuntu          #   + postprocessing script for all

Should the desired distribution you need be missing, please file an issue
in `one-apps repository <https://github.com/OpenNebula/one-apps>`__


Option 2: Prepare the Virtual Machine Image manually
================================================================================

Step 1. Start a VM with the OS you want to Customize
--------------------------------------------------------------------------------

Supported contextualization packages are available for the OS's described in the :ref:`platform notes <context_supported_platforms>`.

.. include:: install_steps.txt

Step 4. Run Sysprep in Windows Machines
--------------------------------------------------------------------------------

Execute ``sysprep`` to prepare the OS for duplication. You can find more information at:

https://technet.microsoft.com/en-us/library/cc721940(v=ws.10).aspx

Step 5. Power Off the Machine and Save it
--------------------------------------------------------------------------------

After these configuration is done you should power off the machine, so it is in a consistent state the next time it boots. Then you will have to save the image.

If you are using OpenNebula to prepare the image you can use the command ``onevm disk-saveas``, for example, to save the first disk of a Virtual Machine called "centos-installation" into an image called "centos-contextualized" you can issue this command:

.. prompt:: bash $ auto

    $ onevm disk-saveas centos-installation 0 centos-contextualized

Using sunstone web interface you can find the option in the Virtual Machine storage tab.

.. include:: template.txt
