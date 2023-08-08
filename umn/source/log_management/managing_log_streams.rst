:original_name: lts_04_0004.html

.. _lts_04_0004:

Managing Log Streams
====================

A log stream is the basic unit for reading and writing logs. Sorting logs into different log streams makes it easier to find specific logs when you need them.

Up to 100 log streams can be created in a log group. The upper limit cannot be increased. If you cannot create a log stream because the upper limit is reached, you are advised to delete log streams that are no longer needed and try again, or create log streams in a new log group.

Prerequisites
-------------

You have created a log group.

Creating a Log Stream
---------------------

Log streams can be created in two ways. They are automatically created when other services are connected to LTS, or you can create one manually by following the steps described here.

#. On the LTS console, click |image1| on the left of a log group name.

#. Click **Create Log Stream** in the upper left corner of the displayed page, and enter a log stream name. After a log stream is created, its name cannot be changed. A log stream name:

   -  Can contain only letters, digits, hyphens (-), underscores (_), and periods (.).
   -  Cannot start with a period (.) or underscore (_) or end with a period (.).
   -  Can contain 1 to 64 characters.


   .. figure:: /_static/images/en-us_image_0000001459633297.png
      :alt: **Figure 1** Creating a log stream

      **Figure 1** Creating a log stream

   .. note::

      Collected logs are sent to the created log stream. If there are too many logs to collect, you are advised to separate logs into different log streams based on log types, and name log streams in an easily identifiable way.

#. Click **OK**.

   In the log stream list, you can view details of the list, including the log stream name, creation time, and creation type.


   .. figure:: /_static/images/en-us_image_0000001576333032.png
      :alt: **Figure 2** A created log stream

      **Figure 2** A created log stream

   .. note::

      Logs cannot be downloaded from log streams on the LTS console. You need to transfer logs to Object Storage Service (OBS) and download them from the OBS console.

Deleting a Log Stream
---------------------

You can delete a log stream that is no longer needed. Deleting a log stream will also delete the log data in the log stream. Deleted log streams cannot be recovered. Exercise caution when performing the deletion.

.. note::

   -  Before deleting a log stream, check whether any log collection task is configured for it. If there is a log collection task, deleting the log stream may affect log reporting.
   -  If you want to delete a log stream that is associated with a log transfer task, delete the task first.

#. In the log stream list, locate the target log stream and click |image2| in the **Operation** column.

#. Enter **DELETE** and click **OK**.


   .. figure:: /_static/images/en-us_image_0000001459892873.png
      :alt: **Figure 3** Deleting a log stream

      **Figure 3** Deleting a log stream

Other Operations
----------------

-  Adding a log stream to favorites

   Click |image3| in the **Operation** column of a log stream to add the log stream to favorites. The log stream is then displayed in **My Favorites**/**My Favorites (Local Cache)** on :ref:`the console home page <lts_04_1153__en-us_topic_0000001217194912_section1179111313129>`.

.. |image1| image:: /_static/images/en-us_image_0000001217758588.png
.. |image2| image:: /_static/images/en-us_image_0000001543219709.png
.. |image3| image:: /_static/images/en-us_image_0000001262713829.png
