:original_name: lts_04_0506.html

.. _lts_04_0506:

Ingesting APIG Logs to LTS
==========================

LTS can collect logs from APIG.

Prerequisites
-------------

You have created and used an API gateway.

Configuring APIG Log Ingestion in LTS
-------------------------------------

Perform the following operations to configure APIG log ingestion:

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**.
#. Choose **Log Ingestion** > **Ingestion Center** in the navigation pane and click **APIG (API Gateway)**.
#. Select a log stream.

   a. Select a log group from the **Log Group** drop-down list. If there are no desired log groups, click **Create Log Group** to create one.
   b. Select a log stream from the **Log Stream** drop-down list. If there are no desired log streams, click **Create Log Stream** to create one.
   c. Click **Next: Configure APIG**.

#. Click **Configure APIG** to configure APIG on the APIG console. For details, see `Log Analysis <https://docs.otc.t-systems.com/api-gateway/umn/monitoring_and_analysis/log_analysis.html>`__.
#. Click **Next: Configure Log Stream**.

   .. table:: **Table 1** Log stream parameters

      +--------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                | Description                                                                                                                                                               |
      +==========================+===========================================================================================================================================================================+
      | Auto Structure and Index | If this function is enabled, the structuring for the log stream is based on the APIG system template, and the indexing enables quick analysis for all parsed APIG fields. |
      +--------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Submit**.
