:original_name: lts_05_0007.html

.. _lts_05_0007:

Quick Analysis
==============

Monitoring keywords in logs helps you keep track of system performance and services. For example, the number of **ERROR** keywords indicates the system health, and the number of **BUY** keywords indicates the sales volume. LTS provides quick analysis for you to obtain statistics on your specified keywords.

Prerequisites
-------------

Quick analysis is conducted on fields extracted from structured logs. :ref:`Structure raw logs <lts_0821>` before you create a quick analysis task.

Creating a Quick Analysis Task
------------------------------

You can enable **Quick Analysis** for the fields on the **Log Structuring** page. You can also perform the following steps to create a quick analysis task:

#. Log in to the LTS console. In the navigation pane on the left, choose **Log Management**.
#. A quick analysis is performed on a log stream. Select the target log group and log stream on the **Log Management** page.
#. Click **Set Quick Analysis** or |image1|. On the displayed page, add fields for quick analysis.
#. Click **OK**. The quick analysis task is created.

   .. note::

      -  |image2| indicates a field of the **string** type.
      -  |image3| indicates a field of the **float** type.
      -  |image4| indicates a field of the **long** type.
      -  The maximum length of a field for quick analysis is 2000 bytes.
      -  The quick analysis field area displays the first 100 records.
      -  Click |image5| in the upper right corner of the **Quick Analysis** area to modify or delete an existing field. If you delete a field or modify the name of a field on the **Log Structuring** page, the field will be updated in the quick analysis.

.. |image1| image:: /_static/images/en-us_image_0000001309911389.png
.. |image2| image:: /_static/images/en-us_image_0000001588482889.png
.. |image3| image:: /_static/images/en-us_image_0000001298698089.png
.. |image4| image:: /_static/images/en-us_image_0000001252258790.png
.. |image5| image:: /_static/images/en-us_image_0000001252099070.png
