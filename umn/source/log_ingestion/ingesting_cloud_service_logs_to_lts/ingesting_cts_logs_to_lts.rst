:original_name: lts_04_0505.html

.. _lts_04_0505:

Ingesting CTS Logs to LTS
=========================

LTS can collect logs from CTS.

Configuring CTS Log Ingestion in LTS
------------------------------------

Perform the following operations to configure CTS log ingestion:

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**.
#. Choose **Log Ingestion** > **Ingestion Center** in the navigation pane and click **CTS (Cloud Trace Service)**.
#. Select a log stream.

   a. Select a log group from the **Log Group** drop-down list. If there are no desired log groups, click **Create Log Group** to create one.
   b. Select a log stream from the **Log Stream** drop-down list. If there are no desired log streams, click **Create Log Stream** to create one.
   c. Click **Next: Configure CTS**.

#. Click **Configure CTS**. For details, see `Configuring a Tracker <https://docs.otc.t-systems.com/cloud-trace-service/umn/user_guide/tracker_management/configuring_a_tracker.html#cts-03-0002>`__.
#. Click **Next: Configure Log Stream**.

   .. table:: **Table 1** Log stream parameters

      +--------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                | Description                                                                                                                                                             |
      +==========================+=========================================================================================================================================================================+
      | Auto Structure and Index | If this function is enabled, the structuring for the log stream is based on the CTS system template, and the indexing enables quick analysis for all parsed CTS fields. |
      +--------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Submit**.
