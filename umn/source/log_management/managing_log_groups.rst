:original_name: lts_04_0003.html

.. _lts_04_0003:

Managing Log Groups
===================

A log group is a group of log streams which share the same log retention settings. Up to 100 log groups can be created for a single account.

Creating a Log Group
--------------------

#. Log in to the LTS console, choose **Log Management** in the navigation pane on the left, and click **Create Log Group** in the upper right corner.

   |image1|

#. In the dialog box displayed, enter a log group name. After a log group is created, its name cannot be changed. A log group name:

   -  Can contain only letters, digits, hyphens (-), underscores (_), and periods (.).
   -  Cannot start with a period (.) or underscore (_), and cannot end with a period (.).
   -  Can contain 1 to 64 characters.

   .. note::

      Collected logs are sent to the log streams in the log group. If there are too many logs to collect, you are advised to separate logs into different log groups based on log types, and name log groups in an easily identifiable way.

#. Log retention duration is 7 days by default and cannot be modified.

   |image2|

#. Click **OK**.

#. In the log group list on the **Log Management** page, you can view details of the log group, including log group name, log retention duration, creation time, and creation type.

Deleting a Log Group
--------------------

You can delete a log group that is no longer needed. Deleting a log group will also delete the log streams and log data in the log group. Deleted log groups cannot be recovered. Exercise caution when performing the deletion.

.. note::

   If you want to delete a log group that is associated with a log transfer task, delete the task first.

#. In the log group list on the **Log Management** page, locate the target log group and click **Delete** in the **Operation** column.
#. Enter **DELETE** and click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0000001368010788.png
.. |image2| image:: /_static/images/en-us_image_0000001419010601.png
