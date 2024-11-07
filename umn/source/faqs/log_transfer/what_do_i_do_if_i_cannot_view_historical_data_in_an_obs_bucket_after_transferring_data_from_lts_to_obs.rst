:original_name: lts_faq_0142.html

.. _lts_faq_0142:

What Do I Do If I Cannot View Historical Data in an OBS Bucket After Transferring Data from LTS to OBS?
=======================================================================================================

This occurs because LTS only transfers logs generated after you configure the transfer task to OBS buckets. Logs that already exist before the configuration will not be transferred.
