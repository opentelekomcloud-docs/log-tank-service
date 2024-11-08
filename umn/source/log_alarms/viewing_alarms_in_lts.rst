:original_name: lts_04_0060.html

.. _lts_04_0060:

Viewing Alarms in LTS
=====================

LTS allows you to configure keyword alarm rules to periodically query log data. When an alarm rule is met, an alarm will be reported. You can view the alarms on the LTS console.

Prerequisites
-------------

You have created an alarm rule.

Procedure
---------

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**.

#. Choose **Alarms** in the navigation pane.

#. Click the **Alarms** tab. The alarms generated in 30 minutes from now and their trend charts are displayed by default.

#. Set criteria to search for your target alarms.

   -  In the search box above the alarm list, select a log group, log stream, and alarm severity.

   -  Set a time range. By default, 30 minutes is specified (relative time from now).

      There are three types of time range: relative time from now, relative time from last, and specified time. Select a time range as required.

      .. note::

         -  From now: queries log data generated in a time range that ends with the current time, such as the previous 1, 5, or 15 minutes. For example, if the current time is 19:20:31 and 1 hour is selected as the relative time from now, the charts on the dashboard display the log data that is generated from 18:20:31 to 19:20:31.
         -  From last: queries log data generated in a time range that ends with the current time, such as the previous 1 or 15 minutes. For example, if the current time is 19:20:31 and 1 hour is selected as the relative time from last, the charts on the dashboard display the log data that is generated from 18:00:00 to 19:00:00.
         -  **Specified**: queries log data that is generated in a specified time range.

#. Click |image1| after you set the search criteria. The details and trend of the alarms that match the criteria will be displayed.

#. You can point to the **Details** column of an alarm on the **Active Alarms** tab to view the complete alarm details. Alternatively, click the name in the **Alarm Name** column of an alarm. Details about the alarm are displayed in the right panel that pops up.

   After the reported fault is rectified, you can click the deletion button in the row that contains the corresponding alarm on the **Active Alarms** tab to clear the alarm. The cleared alarm will then be displayed on the **Historical Alarms** tab.

   If you have configured search criteria to filter alarms, you need to manually refresh the alarm list. To enable automatic refresh, click |image2| in the upper right corner and select **Refresh Every 30s**, **Refresh Every 1m**, or **Refresh Every 5m** from the drop-down list box. You can still manually refresh the alarm list when automatic refresh is enabled by selecting **Refresh Now** from the drop-down list box.

.. |image1| image:: /_static/images/en-us_image_0000001381829696.png
.. |image2| image:: /_static/images/en-us_image_0000001432189445.png
