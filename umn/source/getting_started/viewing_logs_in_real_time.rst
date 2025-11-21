:original_name: lts_08303.html

.. _lts_08303:

Viewing Logs in Real Time
=========================

After the log ingestion is configured, you can view the reported logs on the LTS console in real time.

Prerequisites
-------------

-  You have created log groups and log streams.
-  You have installed ICAgent.
-  You have ingested logs.


Viewing Logs in Real Time
-------------------------

To view real-time logs, stay on the **Real-Time Logs** tab. If you leave the **Real-Time Logs** tab, logs will stop being loaded in real time.

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**.

#. Click the name of an existing log group or log stream to access the log stream details page.

#. Click the **Real-Time Logs** tab to view logs in real time.

   Logs are reported to LTS once every 5 seconds. You may wait for at most 5 seconds before the logs are displayed.

   You can perform the following operations on the reported real-time logs:

   -  Select **Host** for **Source** and set a host IP address and file path to filter logs.

   -  Select **Host** for **K8s** and set an instance or container name or a file path to filter logs.

   -  **Filter**: Select fields to filter field information obtained from the index configurations, structuring configurations, and latest logs.

   -  **Clear**: Displayed logs will be cleared from the real-time view.

   -  **Pause**: Loading of new logs to the real-time view will be paused.

      After you click **Pause**, the button changes to **Continue**. You can click **Continue** to resume the log loading to the real-time view.
