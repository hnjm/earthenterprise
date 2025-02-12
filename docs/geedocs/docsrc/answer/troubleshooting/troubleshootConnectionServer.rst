|Google logo|

=====================================
Troubleshoot connection to GEE Server
=====================================

.. container::

   .. container:: content

      If the Google Earth EC is unable to connect to your GEE Server, you will
      see the error, "Google Earth failed to connect to database":

      To resolve this issue, try these troubleshooting steps:

      #. Make sure the **Server URL** (``http://hostname/path``) is
         correct in the "Google Earth - Select Server" dialog box, which
         appears when you start EC:

         -  The hostname should match the fully qualified domain name of
            your GEE Server.
         -  The path in the URL should match the **Publish Point** shown
            in the GEE Server UI. This path indicates the location where
            the database was published.

      #. Look for client EC requests in the GEE Server logs:

         #. Open a terminal window on the GEE Server.
         #. Type the command
            ``tail -f /opt/google/gehttpd/logs/access_log``
         #. Start EC and try connecting to your GEE Server.
            In the terminal window, you should see time-stamped access
            requests in the logs from the client, starting with a GET
            request for the ``dbRoot`` file, followed by ``flatfile``
            requests—for example:

            ``192.168.1.199 - - [08/Feb/2016:09:10:25 -0800] "GET /3d/dbRoot.v5?hl=en&gl=us&output=proto&cv=7.1.5.1557&ct=ec HTTP/1.1" 200 4512 "-" "GoogleEarth/7.1.5.1557(Windows;Microsoft Windows (6.2.9200.0);en;kml:2.2;client:EC;type:default)" 192.168.1.199 - - [08/Feb/2016:09:10:27 -0800] "GET /3d/dbRoot.v5?db=tm&hl=en&gl=us&output=proto&cv=7.1.5.1557&ct=ec HTTP/1.1" 200 1161 "-" "GoogleEarth/7.1.5.1557(Windows;Microsoft Windows (6.2.9200.0);en;kml:2.2;client:EC;type:default)"``
            
            ``192.168.1.199 - - [08/Feb/2016:09:10:27 -0800] "GET /3d/flatfile?lf-0-icons/help_l.png&h=32 HTTP/1.1" 200 426 "-" "GoogleEarth/7.1.5.1557(Windows;Microsoft Windows (6.2.9200.0);en;kml:2.2;client:EC;type:default)"``
            
            ​If no new entries appear in the logs, then EC was unable to
            establish a connection to the GEE Server. This may be due to
            a network or firewall problem, as described in the next
            step.

      #. Verify network connectivity from EC to the GEE Server:

         -  The firewall on the host might be blocking outbound
            connections - check your firewall. Also, you can use
            tools such as Wireshark or
            `Fiddler <http://www.telerik.com/fiddler>`_ to capture HTTP
            traffic on your computer and confirm that EC is sending
            requests to the GEE Server.
         -  The firewall on the GEE Server might be blocking inbound
            connections from external hosts on port 80. Check whether
            firewalls like ``iptables`` are enabled on the server and
            are configured with packet-filtering rules.
         -  Network or web proxies might be causing connection issues.
            Consult your network administrator.
         -  Use tools such as ``ping`` or ``traceroute`` on the client
            machine to diagnose connectivity issues.

.. |Google logo| image:: ../../art/common/googlelogo_color_260x88dp.png
   :width: 130px
   :height: 44px
