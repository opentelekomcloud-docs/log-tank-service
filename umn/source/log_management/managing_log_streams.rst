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

#. On the LTS console, click the name of the created log group.

#. Click **Create Log Stream** in the upper left corner, and enter a log stream name. After a log stream is created, its name cannot be changed. A log stream name:

   -  Can contain only letters, digits, hyphens (-), underscores (_), and periods (.).
   -  Cannot start with a period (.) or underscore (_), and cannot end with a period (.).
   -  Can contain 1 to 64 characters.

   |image1|

   .. note::

      Collected logs are sent to the created log stream. If there are too many logs to collect, you are advised to separate logs into different log streams based on log types, and name log streams in an easily identifiable way.

#. Click **OK**.

   On the log stream page, you can view details of the log stream, including log stream name, creation time, and creation type.

   .. note::

      Logs cannot be downloaded from log streams on the LTS console. You need to transfer logs to Object Storage Service (OBS) and download them from the OBS console.

Deleting a Log Stream
---------------------

You can delete a log stream that is no longer needed. Deleting a log stream will also delete the log data in the log stream. Deleted log streams cannot be recovered. Exercise caution when performing the deletion.

.. note::

   -  Before deleting a log stream, check whether any log collection task is configured for it. If there is a log collection task, deleting the log stream may affect log reporting.
   -  If you want to delete a log stream that is associated with a log transfer task, delete the task first.

#. In the log stream list, locate the target log stream and click **Delete** in the **Operation** column.
#. Enter **DELETE** and click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0000001419012101.png
