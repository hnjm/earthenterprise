|Google logo|

=============================
Release notes: Open GEE 5.2.1
=============================

.. container::

   .. container:: content

      .. rubric:: Overview

      Open GEE 5.2.1 is a comprehensive update of :doc:`Open GEE
      5.2.0 <../releaseNotes/relNotesGEE5_2_0>`. It contains new features,
      several bug fixes in Fusion and GEE Server, and updates to
      third-party libraries.

      .. rubric:: New Features

      **MrSID support**. At build time, Open GEE checks for MrSID
      libraries and, if found, Fusion will be built with MrSID raster
      format support.

      **RPM Installers**. For RedHat and CentOS, RPMs can now be built
      to enable easier installation. For Ubuntu, the installer scripts
      continue to be the supported way to install Open GEE.

      **JPEG2000 performance boost**. Updated version of OpenJpeg2000
      library has considerable performance increase.

      **Controlling quality of terrain**. Command-line tool gepackgen
      producing packets now accepts a decimation value. In general,
      reducing the decimation value for terrain produces higher quality
      and better looking terrain.

      **Testing scripts enhanced**. ``publish_tutorial.sh`` and
      ``publish_historical.sh`` scripts now publish the pushed
      databases.

      **Detailed version info**. Version number displayed in user
      interface shows detailed information indicating an official
      release or a development build.

      **Continuous Integration**. Travis CI is used for continuous
      integration. On every new commit to Open GEE a build is executed
      to validate the committed changes.

      .. rubric:: Supported Platforms

      Open GEE 5.2.1 is supported on 64-bit versions of the following
      operating systems:

      -  Red Hat Enterprise Linux version 6.x and 7.x, including the
         most recent security patches
      -  CentOS 6.x and 7.x
      -  Ubuntu 14.04 LTS and 16.04 LTS

      Google Earth Enterprise 5.2.1 is compatible with Google Earth
      Enterprise Client (EC) version 7.1.5 and above.

      .. rubric:: New and Updated Libraries

      Open GEE 5.2.1 includes many library updates. Major updates
      include:

      .. list-table::
         :widths: 25 25 25
         :header-rows: 1

         * - Library
           - Version
           - New or Updated
         * - OpenJPEG
           - 2.3.0
           - Updated
         * - PostgreSQL
           - 9.6.5
           - Updated
         * - PostGIS
           - 2.3.4
           - Updated

      To upgrade from Open GEE 5.2.0, do NOT uninstall it. We recommend
      that you upgrade Open GEE 5.2.0 by simply installing Open GEE
      5.2.1. Installing Open GEE 5.2.1 on top of Open GEE 5.2.0 will
      ensure that your PostgreSQL databases are backed-up and upgraded
      correctly to the new PostgreSQL version used by Open GEE 5.2.1.

      .. rubric:: Known Issues

      .. list-table:: Known Issues
         :widths: 25 25 50
         :header-rows: 1

         * - Number
           - Description
           - Workaround
         * - 4
           - Google basemap fails to load in 2D Mercator Maps
           - Obtain a valid Google Maps API key and include it in ``/opt/google/gehttpd/htdocs/maps/maps_google.html``.
         * - 8
           - Ensure GEE Portable Cutter Job Completes
           - No current work around.
         * - 9
           - Improve FileUnpacker Handling of Invalid Files
           - No current work around.
         * - 20
           - Simplify build process for portable builds on MacOS
           - Building and running Portable Server on MacOS should be possible with minimal changes.
         * - 34
           - Scons build creates temporary directories named “0”
           - No current work around.
         * - 126
           - The Fusion installer creates a backup on the first run
           - No current work around. The created backup can be deleted.
         * - 127
           - Incorrect error messages from Fusion installer
           - No current work around.
         * - 190
           - Hostname mismatch check in installers doesn't work as expected
           - No current work around.
         * - 193
           - Updated docs are not copied if the ``/tmp/fusion_os_install`` directory already exists
           - Delete ``/tmp/fusion_os_install`` at the beginning of the stage_install build process.
         * - 200
           - stage_install fails on the tutorial files when ``/home`` and ``/tmp`` are on different file systems
           - Ensure that ``/home`` and ``/tmp`` are on the same file system or download
             the tutorial files to ``/opt/google/share/tutorials/fusion/`` after installing Fusion.
         * - 201
           - Some tiles are displayed incorrectly in the Enterprise Client when terrain is enabled
           - No current work around.
         * - 202
           - Icons are not displayed on vector layers in the Enterprise Client
           - No current work around. It is not clear if this is an error in GEE or in the Enterprise Client.
         * - 203
           - Some vector layer options are not saved
           - No current work around.
         * - 221
           - The asset manager may display that a job is "Queued" when in fact the job is "Blocked"
           - No current work around.
         * - 225
           - Fusion lets you create folder with space in the name
           - Avoid creating folder with space in their name.
         * - 234
           - Geserver raises error executing apache_logs.pyc
           - No current work around.
         * - 254
           - Automasking fails for images stored with UTM projection
           - Use GDAL to convert the images to a different projection before ingesting them into Fusion.
         * - 269
           - gevectorimport doesn't crop features
           - Use GDAL/OGR to crop vector dataset before importing them using Fusion.
         * - 295
           - Fix buffer overflows and leaks in unit tests
           - No current work around.
         * - 309
           - Check for the FusionConnection before new asset is populated
           - Make sure that gefusion service is started.
         * - 320
           - The Portable Server web page uses obsolete REST calls
           - Do not use the buttons on the Portable Server web interface for adding remote
             servers or broadcasting to remote servers as these features are no longer supported.
         * - 326
           - Libraries may be loaded from the wrong directory
           - Delete any library versions that should not be loaded or use LD_LIBRARY_PATH to load
             libraries from ``/opt/google/lib``.
         * - 340
           - GE Fusion Terrain is black
           - No current work around.
         * - 342
           - Fusion crashes when opening an unsupported file type
           - Re-open Fusion and avoid opening unsupported file types.
         * - 343
           - gefusion: File ->open->kiasset,ktasset,kip does not work
           - kip is not a supported format. Void opening files with .kip extension.
         * - 380
           - Provider field in resource-view is blank
           - Open the individual resource to see the provider.
         * - 401
           - GEE commands are not in the path for sudo.
           - Specify the full path when running commands or add ``/opt/google/bin``
             to the path for all users, including the super user.
         * - 402
           - Provider manager window locked to main window.
           - No current work around.
         * - 403
           - Missing close button on system manager window in RHEL 7
           - Right click the title bar and select close.
         * - 404
           - Opaque polygons in preview.
           - No current work around.
         * - 405
           - Vector layer preview not cleared in some situations
           - Reset the preview window to the correct state by either clicking on it or previewing another vector layer.
         * - 407
           - Corrupt data warning when starting Fusion
           - No current work around but Fusion loads and runs correctly.
         * - 419
           - Fix Fusion Graphics Acceleration in Ubuntu 14 Docker Container Hosted on Ubuntu 16
           - No current work around.
         * - 437
           - Rebooting VM while it is building resources results in a corrupted XML
           - No current work around.
         * - 439
           - Uninstalling Fusion without stopping it results in unexpected error message
           - Ignore that error message.
         * - 440
           - Fuzzy imagery in historical imagery tests.
           - No current work around.
         * - 442
           - Multiple database pushes after upgrade don't report a warning
           - No current work around.
         * - 444
           - Fusion installer does not upgrade the asset root on RHEL 7
           - Upgrade the asset root manually by running the command that is printed when you try to start the Fusion service.
         * - 445
           - Path to tutorial source volume in gee_test instructions is different from path used in installers
           - Use ``/opt/google/share/tutorials``.
         * - 448
           - Investigate Out of Memory issues
           - Use a system that has more than 4GB RAM.
         * - 453
           - Improve \`check_server_processes_running\` detection for uninstall
           - No current work around.
         * - 456
           - Inconsistent behavior of vector layers after upgrade
           - No current work around.
         * - 460
           - Possibility of seg fault in QDateWrapper
           - No current work around.
         * - 474
           - Running gee_check on some supported platforms reports that the platform is not supported
           - You can ignore the failed test if using a supported platform (Ubuntu 14.04, Ubuntu 16.04, RHEL 7, and CentOS 7).
         * - 477
           - 'service geserver stop/start/restart' doesn't work on Ubuntu 16.04 without a reboot
           - Reboot and try again.
         * - 487
           - gdal - python utilities do not recognize osgeo module
           - Install ``python-gdal``.
         * - 507
           - Volume host is reported unavailable if \`hostname\` doesn't match volume host
           - Set the host values in ``/gevol/assets/.config/volumes.xml`` to the FQDN and restart the Fusion service.
         * - 535
           - DownloadTutorial.sh often is not staged properly for install
           - Copy ``DownloadTutorial.sh`` to ``/tmp/fusion_os_install``.
         * - 557
           - WMS service problem with 'width' & 'height' & 'bbox'
           - No current work around.
         * - 569
           - geserver service installation and uninstallation issues
           - Before uninstalling geserver verify if it is running or not.
         * - 590
           - Maps API JavaScript Files Not Found
           - No current work around.
         * - 594
           - Save errors only reported for the first image
           - Close the form in question and try again.
         * - 640
           - Save button disabled in 'Map Layer' creation dialog when an error encountered
           - Close the resource form and open it again to make the save option available again.
         * - 651
           - Release executables and libraries depend on gtest
           - Follow current build instructions that requires ``gtest`` to be installed.
         * - 669
           - Missing repo in RHEL 7 build instructions
           - Enable ``rhel-7-server-optional-rpms`` and ``rhel-7-server-optional-source-rpms`` repos.
         * - 682
           - Update geconfigurepublishroot to fully correct file permissions
           - Correct manually the file permissions.
         * - 686
           - Scons fails to detect libpng library on CentOS 6
           - Ensure that a default ``g++`` compiler is installed.
         * - 694
           - Search fails after transferring and publishing a database using disconnected send from the command line
           - Re-publish the database from the web interface.
         * - 700
           - Add EL6/EL7 check to RPMs
           - Make sure that RPMS are installed on same EL version that they were produced for.


      .. rubric:: Resolved Issues

      .. list-table:: Resolved Issues
         :widths: 25 25 50
         :header-rows: 1

         * - Number
           - Description
           - Resolution
         * - 2
           - MrSID imagery is not supported
           - Build script now checks for MrSID libraries and if found, Fusion will be built with MrSID format support
         * - 6
           - The Portable UI reports an error any time a cut is canceled, even if the cancel was successful
           - Fixed concurrency issue
         * - 247
           - Default Imagery and Terrain file filters ignore files with the ".tiff" extension
           - Added ".tiff" to list of supported format extensions
         * - 321, 335, 359
           - If there is an error while saving a resource, the resource cannot be saved again even if the error is resolved
           - Fixed out-of-sync errors
         * - 355
           - Package gtest under CentOS/RHEL 6
           - instructions for building OpenGEE under CentOS 6 were updated and build scripts
             modified to detect and use "devtoolset-2-toolchain"
         * - 375
           - Invalid version of psycopg2 on Ubuntu 16.04
           - Added PYTHONPATH to Apache environment, so it gets passed on to CGI scripts like Cutter
         * - 423
           - Slower JPEG2000 performance than 5.1.3
           - Upgraded to new version of OpenJpeg: 2.3.0. This new version has multiple performance improvements.
         * - 476
           - Support building on CentOS6 with Python2.6
           - Added support for Python 2.6 for CentOS6.
         * - 515
           - gepolymaskgen segfaults with specific inputs
           - Fixed out of bounds error in box filter
         * - 524
           - Globe Database Fails to Publish if a Snippet is selected
           - Fixed spelling mistake
         * - 624
           - File permissions incorrect in ``/opt/google`` if root has a restrictive umask
           - Fixed permissions
         * - 634
           - Duplicate resources in imagery projects
           - Passed "re_init" flag down through prefill
         * - 658
           - Fix Perl Interpreter Paths in Built Scripts
           - Added initscripts as a dependency for opengee-server and
             updated find-requires and requiresCommands capabilities of RPM
         * - 666
           - Running gerewritedbroot with the proper parameters results in a usage message
           - initialized variable in gerewritedbroot
         * - 668
           - Cannot push databases with search enabled in dual server configuration
           - Ensured that poi data files are included in the manifest when pushing a database to the server
         * - 671
           - Documentation link on Server admin page is broken in release_5.2.1
           - Fixed links
         * - 677, 685
           - Trying to disassemble or assemble a portable globe or map GLC fails on RedHat 6
           - Used a python 2.6 compatible function instead of python 2.7.
         * - 680
           - Restoring a DB dump from earlier versions of GEE that does not have a search enabled will fail
           - Moved logic to add postgres extension when restoring/upgrading earlier in the process

.. |Google logo| image:: ../../art/common/googlelogo_color_260x88dp.png
   :width: 130px
   :height: 44px
