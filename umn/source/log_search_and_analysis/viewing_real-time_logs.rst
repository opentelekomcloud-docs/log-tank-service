:original_name: lts_05_0006.html

.. _lts_05_0006:

Viewing Real-Time Logs
======================

Logs are reported to LTS about every minute, allowing you to view them on the **Real-Time Logs** page within one minute after configuring log ingestion. This enables rapid search and analysis.

Prerequisites
-------------

Logs have been reported to the **Real-Time Logs** page.


Viewing Real-Time Logs
----------------------

Stay on the **Real-Time Logs** tab page to keep updating them in real time. If you leave the **Real-Time Logs** tab page, logs will stop being loaded. The next time you access the tab page, the logs that were shown before you left the tab page will not be displayed.

Log data is usually loaded every 5 seconds. However, if no data is generated in a 5-second interval, no new data will be displayed. Log data will be updated in the next 5 seconds if there is new data coming in that interval.

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**. The **Log Management** page is displayed by default.

#. Click the target log group or stream to access the log details page.

#. Click the **Real-Time Logs** tab.

   Logs are reported to LTS once every minute. You may wait for at most 1 minute before the logs are displayed.

   You can perform the following operations on the reported real-time logs:

   -  Select **Host** for **Source** and set a host IP address and file path to filter logs.

   -  Select **Host** for **K8s** and set an instance or container name or a file path to filter logs.

   -  **Filter**: Select fields to filter field information obtained from the index configurations, structured configurations, and latest logs.

   -  **Clear**: Clear all logs displayed in the **Log Content** area.

   -  **Pause**: Pause the loading of new logs to the real-time view.

      After you click **Pause**, the button changes to **Continue**. You can click **Continue** to resume the log loading to the real-time view.
