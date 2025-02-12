|Google logo|

=============================================
System requirements for Fusion and GEE Server
=============================================

.. container::

   .. container:: content

      .. rubric:: Hardware Requirements

      -  Minimum 2 dual-core Intel or AMD CPUs; 2.0 GHz or higher
         recommended.
      -  Minimum 4 GB RAM (8 GB RAM for Red Hat Enterprise Linux);
         8 GB RAM (or more) per core recommended for Fusion.
      -  Minimum 500 GB of total hard disk storage.
      -  A graphics card with at least 64 MB video RAM (NVIDIA
         GeForce4 or higher preferred for Fusion GUI). You can
         install this graphics card in a separate workstation that
         accesses Fusion.

      **Note:** If you plan on cutting globes, this processing can
      be CPU-intensive and you may also need to plan on providing
      more storage depending on the size of the globes.

      **Note on virtual machines**: Fusion can be both CPU and I/O
      intensive. For optimal, stable performance, you should
      install it only on physical (non-virtual) machines. You can
      run GEE Server on a virtualized platform, provided the guest
      OS is one of our supported 64-bit distributions and you
      allocate sufficient resources to the VM.

      .. rubric:: Software Requirements

      **Operating Systems**

      Google Earth Enterprise is supported only on the 64-bit
      versions of the operating systems listed below.

         -  Red Hat Enterprise Linux 6.x and 7.x, including the most
            recent security patches
         -  CentOS 6.x and 7.x
         -  Ubuntu 14.04 LTS and 16.04 LTS

      **Browsers**

      Google Earth Enterprise is supported on the following
      browsers on all operating systems:

         -  The latest version of Google Chrome
         -  The latest version of Mozilla Firefox

      However, Google Earth Enterprise should work with any modern
      browser.

      **Google Earth Enterprise Client (EC)**

      The following versions of Google Earth Enterprise Client
      (EC) are recommended for use with Google Earth
      Enterprise:

         -  Version 5.x, use Google Earth EC version 7.0 or later
         -  Version 4.4, use Google Earth EC version 6.1 or later

      .. note::

         Although older versions of Google Earth EC,
         i.e., 6.0 and earlier, *may* still connect to Google
         Earth Enterprise or Portable 3D databases, not all
         features will be available. Also, as Google Earth
         Enterprise has not been tested or certified against older
         versions of Google Earth EC, there may be unknown
         operational problems.

      Google Earth Enterprise Client (EC) is supported on the
      following platforms:

      -  Windows
      -  Mac
      -  Linux

      **Unsupported Versions and Environments**

      There are many variations of operating systems and related
      software; point ("x.x") releases can sometimes contain
      changes that can impact your GEE installation. Although an
      unsupported version of these software packages may appear to
      function correctly, their use in a production environment is
      not recommended. Unexpected results may occur.

      Where possible, you should adhere to the hardware and
      software specifications listed in this document. If a
      problem arises in an unsupported configuration, we may not
      be able to help you resolve it.

      .. rubric:: Network Requirements

      Each destination server must meet the requirements below
      before you install GEE, and you must not change these
      settings after deploying GEE. The hostname must be the FQDN
      (Fully Qualified Domain Name) of your destination server, e.g.,
      ``myserver.mydomainname.com``. Refer to :doc:`Hostname FQDN
      Configuration <../installGEE/hostnameFQDNConfig>`
      for additional details.

      You can verify the hostname of your workstation by entering
      ``hostname`` at a shell prompt, and you can verify the
      network connection by using the ``ping`` command to reach
      other hosts in the same network. The requests should resolve
      using both and IP address and the FQDN.

         -  Hostname registered in DNS
         -  Hosts file is acceptable for small-scale systems
         -  Allocated IP addresses
         -  Correct network routing paths
         -  Network connectivity (Ports 80 and 22; Port 443 for
            HTTPS)
         -  Default installation of a Supported OS
         -  Java Development Kit or Runtime Environment (must
            download from Sun; use version 1.6.0_12 or newer)
         -  OpenSSL 0.9.8y (on OS media)
         -  Python 2.7.5 (on OS media)
         -  Storage for all source data and asset tree
         -  May be local storage (i.e., RAID 5 array)
         -  NAS storage via NFS acceptable
         -  SAN storage acceptable
         -  USB drive not recommended

      .. rubric:: Supported Configurations

      Google Earth Enterprise products are developed per the
      hardware and software requirements listed above. The
      products are intended to be installed according to the
      processes described in this documentation. When installing
      Google Earth Enterprise in an unsupported environment, there
      are risks that the products may not operate as intended.

      Some factors that could affect your installation and
      deployment are:

      -  Installations on unsupported operating systems.
      -  Improperly configured DNS.
      -  Third party or non-default permissions or security measures
         (no root access, sudo blockers, etc.).
      -  Complex proxy configurations that prevent the network
         communications from operating as intended.

      .. rubric:: Important System Security Information

      We strongly recommend that users who wish to host 3D and 2D
      globes online with Google Earth Enterprise follow
      industry standard security practices and review their
      systems and networks before enabling access. Although we
      takes every precaution to secure the information, there is
      always the risk of unauthorized access outside of a closed
      or protected network.

.. |Google logo| image:: ../../art/common/googlelogo_color_260x88dp.png
   :width: 130px
   :height: 44px
