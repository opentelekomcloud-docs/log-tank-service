:original_name: lts_04_0011.html

.. _lts_04_0011:

Overview
========

After being reported from hosts and cloud services to LTS, logs will be retained in LTS for the retention period you specify. Once this period ends, LTS will delete them. You can specify the retention period when creating a log group or stream. For details, see :ref:`Managing Log Groups <lts_04_0003>` and :ref:`Managing Log Streams <lts_04_0004>`. Retained logs are deleted once the period is over. For long-term storage or persistent logging, you can transfer logs to other cloud services.

Log transfer refers to when logs are replicated to other cloud services. LTS deletes retained logs once the retention period is over, but the logs that have been transferred to other services are not affected.
