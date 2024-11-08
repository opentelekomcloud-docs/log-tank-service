:original_name: lts_08302.html

.. _lts_08302:

Ingesting Logs
==============

The following shows how you can ingest host logs to LTS.

When ICAgent is installed, configure the paths of host logs that you want to collect in log streams. ICAgent will pack logs and send them to LTS in the unit of log streams.

Prerequisites
-------------

-  You have created log groups and log streams.
-  You have installed ICAgent.

Procedure
---------

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**.

#. In the navigation pane, choose **Log Ingestion**.

#. Click **ECS (Elastic Cloud Server)** to configure log ingestion.

#. Select a log stream.

   a. Select a log group from the drop-down list of **Log Group**. If there are no desired log groups, click **Create Log Group** to create one.
   b. Select a log stream from the drop-down list of **Log Stream**. If there are no desired log streams, click **Create Log Stream** to create one.
   c. Click **Next: (Optional) Select Host Group**.

#. Select one or more host groups.

   a. In the host group list, select one or more host groups to collect logs. If there are no desired host groups, click **Create** in the upper left corner of the list. On the displayed **Create Host Group** page, create a host group. For details, see :ref:`Managing Host Groups <lts_02_1033>`.

      .. note::

         You can skip this step and configure host groups as follows after the ingestion configuration is complete. However, you are advised to configure host groups during the first ingestion to ensure that the collection configuration takes effect.

         -  Choose **Host Management** in the navigation pane, click the **Host Groups** tab, and complete the association.
         -  Choose **Log Ingestion** in the navigation pane, click an ingestion configuration, and make the association on the details page.

   b. Click **Next: Configurations**.

#. Configure the collection.

   For details, see :ref:`Step 3: Configure the Collection <lts_04_1031__en-us_topic_0000001118501736_section196913102330>`.

#. (Optional) Configure structured logs.

#. (Optional) Configure indexes.

#. Click **Submit** Click **Back to Ingestion Configurations** to check the ingestion details. You can also click **View Log Stream** to view the log stream to which logs are ingested.
