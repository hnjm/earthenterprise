|Google logo|

=======================================
Customize your Google Maps landing page
=======================================

.. container::

   .. container:: content

      Google uses the Google Maps API to create a sample web application
      that provides a very basic way to display your Google Maps
      database output in a browser. The sample web application and the
      Google Maps API are automatically installed with Google Earth
      Enterprise Fusion.

      Google recommends that you use the sample application to display
      your Google Maps data at first. After you see how it looks, you
      can create your own Google Maps web application that looks more
      like your other web applications, using the provided sample web
      application as a guide. Documentation for the Google Maps
      JavaScript API is at `Google Maps JavaScript API V3
      Reference <https://developers.google.com/maps/documentation/javascript/reference>`.

      To get started, make a copy of the sample application files
      (``maps_local.html``, ``maps_google.html, fusionmaps.js``, and
      ``fusionmaps.css``). Then configure a virtual host on which you
      can experiment, and move the copied files to that virtual host.
      When you create the Apache configuration file for the new virtual
      host, change ``/maps/maps_google.html`` or
      ``/maps/maps_local.html`` in the following line to point to your
      copy of the example files on the new virtual host:

      ``RewriteRule ^/default_map/+$ /maps/maps_google.html [PT]``
      or

      ``RewriteRule ^/default_map/+$ /maps/maps_local.html [PT]``
      You can edit the rest of the sample application in whatever ways
      you like, adding your own logo, branding, and so on.

      .. rubric:: Configuring the Google Maps API License Key
         :name: configuring-the-google-maps-api-license-key

      Google Maps supports only specific browser/operating system
      combinations. Even if you are using a supported browser, there are
      some features in Google Earth Enterprise Fusion that are not
      supported by some browsers on certain operating systems.

      As long as you are connected to the Internet and have a license
      key for the Google Maps API, there is no problem (regardless of
      your platform), since your server contacts Google’s servers for
      functions that are not supported in the browser.

      **Note:** The following procedure assumes that you have received
      an email from Google that contains your license key for the Google
      Maps API.

      .. rubric:: To configure your Google Maps API license key:
         :name: to-configure-your-google-maps-api-license-key

      #. Open ``/opt/google/gehttpd/htdocs/maps/maps_google.html``.
      #. Locate the following line in the script:

         ::

            <script src="http://maps.google.com/maps?file=api&v=2&key=abcdefg"type="text/javascript"></script>

      #. Replace the ``key`` placeholder ('``abcdefg``') with your
         Google Maps API license key. Your key is contained in an email
         sent from Google.
      #. Save the ``maps_google.html`` file.
      #. Restart the Google Earth Enterprise Server (as root):

         ::

            sudo /etc/init.d/geserver restart


.. |Google logo| image:: ../../art/common/googlelogo_color_260x88dp.png
   :width: 130px
   :height: 44px
