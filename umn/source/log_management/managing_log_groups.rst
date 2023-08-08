:original_name: lts_04_0003.html

.. _lts_04_0003:

Managing Log Groups
===================

A log group is a group of log streams. Up to 100 log groups can be created for a single account.

Creating a Log Group
--------------------

Log groups can be created in two ways. They are automatically created when other services are connected to LTS, or you can create one manually by following the steps described here.

#. Log in to the LTS console, choose **Log Management** in the navigation pane on the left, and click **Create Log Group** in the upper right corner.


   .. figure:: /_static/images/en-us_image_0000001615509865.png
      :alt: **Figure 1** Creating a log group

      **Figure 1** Creating a log group

#. In the dialog box displayed, enter a log group name. After a log group is created, its name cannot be changed. A log group name:

   -  Can contain only letters, digits, hyphens (-), underscores (_), and periods (.).
   -  Cannot start with a period (.) or underscore (_) or end with a period (.).
   -  Can contain 1 to 64 characters.

   .. note::

      Collected logs are sent to the log streams in the log group. If there are too many logs to collect, you are advised to separate logs into different log groups based on log types, and name log groups in an easily identifiable way.

#. Set **Log Retention Duration**. You can set it to 1 to 30 days. If this parameter is not specified, logs are retained for 7 days by default.


   .. figure:: /_static/images/en-us_image_0000001459614217.png
      :alt: **Figure 2** Creating a log group

      **Figure 2** Creating a log group

#. Click **OK**.

   -  In the log group list, you can view details of log groups, including log group name, log retention duration (days), creation type, creation time, and number of log streams.
   -  Click the log group name, the details page of one of its log streams is displayed.
   -  When multiple log groups are created concurrently, there may be a limit exceeding error.

Deleting a Log Group
--------------------

You can delete a log group that is no longer needed. Deleting a log group will also delete the log streams and log data in the log group. Deleted log groups cannot be recovered. Exercise caution when performing the deletion.

.. note::

   If you want to delete a log group that is associated with a log transfer task, delete the task first.

#. In the log group list on the **Log Management** page, locate the target log group and click **Delete** in the **Operation** column.

#. Enter **DELETE** and click **OK**.


   .. figure:: /_static/images/en-us_image_0000001409026272.png
      :alt: **Figure 3** Deleting a log group

      **Figure 3** Deleting a log group

Searching Log Groups/Streams
----------------------------

In the log group list, click the search box and set the following filter criteria:

-  Log group/stream
-  Log group name/ID
-  Log stream name/ID


.. figure:: /_static/images/en-us_image_0000001459871273.png
   :alt: **Figure 4** Searching log groups/streams

   **Figure 4** Searching log groups/streams
