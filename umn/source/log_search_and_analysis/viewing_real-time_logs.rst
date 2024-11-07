:original_name: lts_05_0006.html

.. _lts_05_0006:

Viewing Real-Time Logs
======================

Logs are reported to LTS about every minute, allowing you to view them on the **Real-Time Logs** page within 1 minute after configuring log ingestion. This enables rapid search and analysis.

.. note::

   Log data is usually loaded every 5 seconds. However, if no data is generated in a 5-second interval, no new data will be displayed. Log data will be updated in the next 5 seconds if there is new data coming in that interval.

Prerequisites
-------------

-  You have created log groups and log streams.
-  You have performed operations provided in :ref:`Installing ICAgent (Intra-Region Hosts) <lts_02_0013>`.
-  You have configured log collection rules.


Viewing Real-Time Logs
----------------------

Stay on the **Real-Time Logs** tab page to keep updating them in real time. If you leave the **Real-Time Logs** tab page, logs will stop being loaded. The next time you access the tab page, the logs that were shown before you left the tab page will not be displayed.

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**. The **Log Management** page is displayed by default.

#. Click the target log group or stream. The log stream details page is displayed.

#. Click the **Real-Time Logs** tab to view the real-time logs.

   .. note::

      Filter host and K8s logs by source.

      -  If **Source** is set to **Host**, set the host IP address and file path.
      -  If **Source** is set to **K8s**, set the instance name, container name, and file path.

   Logs are reported to LTS once every minute. You may wait for at most 1 minute before the logs are displayed.

   In addition, you can customize log display by clicking **Clear** or **Pause** in the upper right corner.

   -  **Filter**: Obtain data from the index configuration, structuring configuration, and latest logs.

   -  **Clear**: Displayed logs will be cleared from the real-time view.

   -  **Pause**: Loading of new logs to the real-time view will be paused.

      After you click **Pause**, the button changes to **Continue**. You can click **Continue** to resume the log loading to the real-time view.
