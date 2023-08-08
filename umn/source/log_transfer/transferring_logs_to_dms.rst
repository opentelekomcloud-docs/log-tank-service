:original_name: lts_04_0043.html

.. _lts_04_0043:

Transferring Logs to DMS
========================

You can use DMS APIs to retrieve logs in real time.

Prerequisites
-------------

-  Logs have been ingested to LTS.
-  Before registering a DMS Kafka instance, configure an inbound rule to allow access from **198.19.128.0/17** over port **9011**.

Procedure
---------

#. Log in to the LTS console and choose **Log Transfer** in the navigation pane on the left.
#. Click **Create Log Transfer** in the upper right corner.
#. On the displayed page, configure the log transfer parameters.

   .. note::

      After a transfer task is created, you can modify parameters except the log group name and transfer mode.

   .. table:: **Table 1** Transfer parameters

      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                                                                                                                                         | Example Value         |
      +=======================+=====================================================================================================================================================================================================================================================================================================+=======================+
      | Enable Transfer       | Enabled by default.                                                                                                                                                                                                                                                                                 | Enabled               |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Transfer Destination  | Select a cloud service for log transfer.                                                                                                                                                                                                                                                            | DMS                   |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Log Group Name        | Select a log group.                                                                                                                                                                                                                                                                                 | N/A                   |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Log Stream Name       | Select a log stream.                                                                                                                                                                                                                                                                                | N/A                   |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Kafka Instance        | Select a Kafka instance. If no instances are available, click **View Kafka Instances** to access the DMS console and create a Kafka premium instance.                                                                                                                                               | N/A                   |
      |                       |                                                                                                                                                                                                                                                                                                     |                       |
      |                       | If a Kafka instance has been registered, you can modify it. For details about how to register a Kafka instance, see :ref:`Registering a Kafka Instance <lts_04_0043__en-us_topic_0293459281_en-us_topic_0251986227_en-us_topic_0249044180_section11223519163112>`.                                  |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Topic                 | Select a topic for the Kafka instance. If no topics are available, access the DMS console and create a topic for the Kafka premium instance.                                                                                                                                                        | topic-01              |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Format                | Only the raw log format is supported. The following is an example:                                                                                                                                                                                                                                  | Raw Log Format        |
      |                       |                                                                                                                                                                                                                                                                                                     |                       |
      |                       | (Logs displayed on the LTS console are in the raw format.)                                                                                                                                                                                                                                          |                       |
      |                       |                                                                                                                                                                                                                                                                                                     |                       |
      |                       | .. code-block::                                                                                                                                                                                                                                                                                     |                       |
      |                       |                                                                                                                                                                                                                                                                                                     |                       |
      |                       |    Sep 30 07:30:01 ecs-bd70 CRON[3459]: (root) CMD (/opt/oss/servicemgr/ICAgent/bin/manual/mstart.sh > /dev/null 2>&1)                                                                                                                                                                              |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Log Transfer Interval | Logs are transferred to the Kafka instance in real time.                                                                                                                                                                                                                                            | Real time             |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Filter by Tag Fields  | During transfer, logs will be filtered by tag fields collected by ICAgent.                                                                                                                                                                                                                          | Enabled               |
      |                       |                                                                                                                                                                                                                                                                                                     |                       |
      |                       | -  Disabled: Logs will not be filtered by tag fields.                                                                                                                                                                                                                                               |                       |
      |                       | -  Enabled: Default tag fields include those for hosts (**hostIP**, **hostId**, **hostName**, **pathFile**, and **collectTime**) and for Kubernetes (**clusterName**, **clusterId**, **nameSpace**, **podName**, and **appName**). Optional common tag fields are **regionName** and **projectId**. |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **OK**. When the log transfer status changes to **Normal**, the transfer task has been created. If you transfer logs of another account, the log group and stream belong to the delegator. When you click the name of the delegator's log group or stream on the **Log Transfer** page, you will be directed to the log group or stream through the agency.
#. Click the Kafka premium instance in the **Transfer Destination** column to access its basic information page.

.. _lts_04_0043__en-us_topic_0293459281_en-us_topic_0251986227_en-us_topic_0249044180_section11223519163112:

Registering a Kafka Instance
----------------------------

#. If you select a Kafka instance that is not registered, access the page for registering the Kafka instance.
#. Configure the parameters for registering a Kafka instance.

   +--------------------+-------------------------------------------------------------------------------------------------------+---------------+
   | Parameter          | Description                                                                                           | Example Value |
   +====================+=======================================================================================================+===============+
   | Kafka Instance     | DMS instance name.                                                                                    | Kafka-01      |
   +--------------------+-------------------------------------------------------------------------------------------------------+---------------+
   | Create DMS Network | Connect the Kafka instance to LTS so that LTS can send data through this network.                     | ``-``         |
   +--------------------+-------------------------------------------------------------------------------------------------------+---------------+
   | Username           | If SASL authentication is enabled for the Kafka instance, enter the username for SASL authentication. | DMS           |
   +--------------------+-------------------------------------------------------------------------------------------------------+---------------+
   | Password           | If SASL authentication is enabled for the Kafka instance, enter the password for SASL authentication. | ``-``         |
   +--------------------+-------------------------------------------------------------------------------------------------------+---------------+

#. Click **OK**.
