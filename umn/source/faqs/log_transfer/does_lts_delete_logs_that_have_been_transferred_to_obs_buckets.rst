:original_name: lts_faq_0044.html

.. _lts_faq_0044:

Does LTS Delete Logs That Have Been Transferred to OBS Buckets?
===============================================================

The log transfer function only forwards existing logs and does not delete them. LTS deletes retained logs once the retention period is over, but the logs that have been transferred to other services are not affected.

During log transfer, logs are "replicated" from LTS to OBS. To view transferred log files, click the name of the corresponding OBS bucket on the **Log Transfer** page of the LTS console, and you will be directed to the OBS console to check the files.
