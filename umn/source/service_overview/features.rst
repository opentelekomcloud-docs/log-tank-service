:original_name: lts_01_0004.html

.. _lts_01_0004:

Features
========

Before using LTS, learn its main features in :ref:`Table 1 <lts_01_0004__en-us_topic_0180792001_table16113624193111>`.

.. _lts_01_0004__en-us_topic_0180792001_table16113624193111:

.. table:: **Table 1** Features

   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Feature                           | Description                                                                                                                                                                                                                                                                                                                         |
   +===================================+=====================================================================================================================================================================================================================================================================================================================================+
   | Real-time log collection          | Collects real-time logs and displays them on the LTS console in an intuitive and orderly manner. You can query logs or transfer logs for long-term storage.                                                                                                                                                                         |
   |                                   |                                                                                                                                                                                                                                                                                                                                     |
   |                                   | Collected logs can be structured or unstructured. Log structuring processes logs in log streams by extracting the logs in a fixed format or with a similar pattern based on the extraction rules you set. Then you can use SQL syntax to query the structured logs.                                                                 |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | High-volume storage and search    | Supports log query by keyword or fuzzy match, search of tens of billions of logs in seconds, and iterative search of hundreds of billions of logs.                                                                                                                                                                                  |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Log transfer                      | -  Allows you to transfer logs to OBS for long-term storage. Logs reported from hosts and cloud services are retained in LTS for a custom period. Log transfer is to replicate logs to the target cloud service. The original logs are retained in LTS and will be automatically deleted when the configured retention period ends. |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
