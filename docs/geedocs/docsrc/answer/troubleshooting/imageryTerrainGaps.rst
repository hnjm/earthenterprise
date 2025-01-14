|Google logo|

=======================
Imagery or terrain gaps
=======================

.. container::

   .. container:: content

      Your map imagery or terrain might display one or more of these
      issues:

      -  Small gaps in both imagery and terrain that change as you zoom
         in or out.
      -  Dropoffs to zero values in the terrain at the edges of your
         tiles.
      -  A permanent black seam at the edges of tiles where they meet
         the adjacent tiles.
      -  Gaps or tears in the imagery that appear at seemingly random
         places, and that disappear when the terrain is turned off.

      To resolve these issues:

      -  Make sure that the *input* imagery does not have gaps,
         seamlines, or holes.
      -  If there is usable data to each extent of your imagery, you can
         remove the mask.
      -  By default, the automask tool assumes that the pixel value of
         the green band is the fill data pixel value for the entire
         image. This is used for masking as well as the hole check. Make
         sure that the **Nodata** field contains a ``0``. Do not leave it
         blank.
      -  If placing a ``0`` in the **Nodata** field does not resolve the
         issue, create a mask file manually with the ``gemaskgen``
         command and recreate the ``kmp`` folder in Fusion. See
         instructions below.

      To manually create the mask file:

      #. | Locate and record the full path to the resource ``kip`` and
           ``kmp`` folders:
         | ``gequery --outfiles resources/imagery/resource_i.kiasset``

         You will need this information for building the automask and
         importing the mask product.

      #. Locate the path to the ``mask.tif`` file created by the
         automasker:
         ``gequery --outfiles resources/imagery/resource_i.kiasset/maskgen.kia``
      #. Navigate to the ``mask.tif`` file and rename it to
         ``mask.tif.bak``.
      #. | Create the new mask file:
         | ``gemaskgen --mask --band 1 --fill 0 --feather 0 \ --holesize 100 /path/to/resource_i.kiasset/product.kia/ver/raster.kip \ -o ./mask.tif``

         If your source files are ``MrSID`` files, you might need to add
         a mask tolerance value (e.g., ``--tolerance 3``).

      #. Navigate to the resource ``kip`` and ``kmp`` folders, and move
         the ``mask.kmp`` folder to ``mask.kmp.bak``.
      #. Create the new mask.kmp:
         ``gerasterimport --alphamask /path/to/mask.tif --dataproduct /path/to/raster.kip \ --output ./mask.kmp``
      #. Launch the Fusion GUI and preview the image resource.

.. |Google logo| image:: ../../art/common/googlelogo_color_260x88dp.png
   :width: 130px
   :height: 44px
