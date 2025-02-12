|Google logo|

========================
Release notes: GEE 5.1.3
========================

.. container::

   .. container:: content

      .. rubric:: Overview

      GEE 5.1.3 is an incremental release of
      :doc:`GEE 5.1 <../releaseNotes/relNotesGEE5_1_0>`. It contains several bug fixes in
      Fusion and GEE Server, and updates to third-party libraries.

      .. rubric:: Supported Platforms

      The Google Earth Enterprise 5.1.3 release is supported on 64-bit
      versions of the following operating systems:

      -  Red Hat Enterprise Linux versions 6.0 to 7.2, including the
         most recent security patches
      -  CentOS 6.0 to 7.2
      -  Ubuntu 10.04, 12.04 and 14.04 LTS

      Google Earth Enterprise 5.1.3 is compatible with Google Earth
      Enterprise Client (EC) version 7.1.8 and Google Earth Plug-in
      versions 7.0.1 - 7.1.5.1557 for Windows and Mac.

      .. rubric:: Library Updates

      .. list-table:: Library Updates
         :widths: 30 30
         :header-rows: 1

         * - Library
           - Updated Version
         * - GDAL
           - 2.1.2
         * - Google Maps JS API V3
           - 3.27
         * - Apache httpd
           - 2.2.32
         * - OpenSSL
           - 1.0.2k
         * - freetype
           - 2.6.1

      .. rubric:: Known Issues

      .. list-table:: Known Issues
         :widths: 25 25 50
         :header-rows: 1

         * - Number
           - Description
           - Workaround
         * - 31619151
           - Missing historical imagery dates in EC timeslider
           - Ensure all assets in the project have valid timestamps and
             they are unique (in case some of the resources have the same date & time).
         * - 35093485
           - Google basemap fails to load in 2D Mercator databases built with "Use Google Basemap" option
           - Edit ``/opt/google/gehttpd/htdocs/maps/maps_google.html``
             to include a valid API Key (or client id) to the Maps API JavaScript call.
             See `<https://developers.google.com/maps/documentation/javascript/error-messages#no-api-keys>`_

      .. rubric:: Resolved Issues

      .. list-table:: Resolved Issues
         :widths: 25 25 50
         :header-rows: 1

         * - Number
           - Description
           - Resolution
         * - 1644180
           - Improve granularity of image acquisition date
           - Fixed in Fusion: imagery acquisition date now supports hours, minutes and
             seconds with the (ISO-8601) format ``YYYY-MM-DD hh:mm:ss``. This new extended
             timestamp is backward compatible and enabled in the Fusion UI as well as i
             command-line tools. Client support is being added to EC's timeslider; updated version coming soon.
         * - 11271105
           - ``gekmlgrabber`` fails to grab KML files referenced with relative URLs
           - Fixed in Cutter.
         * - 17300345, 18021264
           - Missing cache_alpha files reported when building projects with pre-processed source data (KIP)
           - Fixed in Fusion: after upgrading, clean the latest blocked version of the database,
             clean the latest blocked version of the imagery/terrain project, and then rebuild.
         * - 21760202
           - gesystemmanager consumes large amount of of resources (cpu & memory) when cancelling large projects
           - Fixed in Fusion: optimized cache when building raster projects.
         * - 24375793
           - Use asynchronous communication with server in Portable Viewer
           - Fixed in Portable Server.
         * - 24469566
           - Search bar disappears after clicking 'go to polygon' in Portable Viewer
           - Fixed in Portable Server.
         * - 25954774
           - Implement swap and replace functions when publishing databases
           - Fixed in GEE Server: to facilitate updates to existing published databases,
             ``geserveradmin`` supports ``--republish`` of databases which involves unpublishing
             an existing target, and publishing a new database on that same target while retaining
             its publish context i.e. virtual host, snippets, search services, WMS-serving.
             The ``--swaptargets`` option swaps the target path of two published databases
             along with their publish context. This makes it easy to test or revert databases
             in production environments. For more information, see ``geserveradmin`` usage.
         * - 26964919, 27346002
           - POI searches fail when servers deployed behind load-balancer
           - Fixed in GEE Server: deprecate database ID (db_id), and modify POI search service to
             query poi_id based on target_path instead.
         * - 27689103
           - Large POI files break database push
           - Fixed in Fusion: Split POI files in 1 GB parts.
         * - 28941507
           - Coordinate search doesn't send search status to Federated search
           - Fixed in GEE Server.
         * - 30189080
           - Security: High risk HTTPoxy vulnerability
           - Fixed in GEE Server: block HTTP Proxy headers in Apache environment.
         * - 30512788
           - Publish fails when only supplementary search tabs are enabled
           - Fixed in GEE Server.
         * - 30974078
           - Portable throws error with blank lines in portable.cfg
           - Fixed in Portable Server.
         * - 31713095
           - Check for duplicate images in Asset Manager
           - Fixed in Fusion: Imagery Resource file dialog checks for duplicates such that the
             same image cannot be added more than once.
         * - 32120563
           - Get postgreSQL port number from configuration file
           - Fixed in GEE Server: custom port numbers for GEE's postgres service should be specified in
             the files: ``/var/opt/google/pgsql/data/postgresql.conf`` and
             ``/opt/google/gehttpd/wsgi-bin/conf/postgres.properties``. (The default port is 5432.)
         * - 32547956
           - Cutter fails if 'rsync' not present on system
           - Fixed in GEE Server: gecutter is no longer dependent on 'rsync' utility.

.. |Google logo| image:: ../../art/common/googlelogo_color_260x88dp.png
   :width: 130px
   :height: 44px
