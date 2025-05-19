:original_name: lts_faq_0070.html

.. _lts_faq_0070:

How Do I Disable the Function of Collecting CCE Standard Output Logs to AOM on the LTS Console?
===============================================================================================

Symptom
-------

As the products evolve, collecting CCE standard output logs to AOM is no longer recommended. You can disable this function on the LTS console as needed. You are advised to collect CCE standard output logs to LTS for unified log management.

Only when the collection of CCE standard output logs to AOM is disabled, the collection of CCE standard output logs to LTS configured on the LTS console will take effect.

Solution
--------

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**.
#. Choose **Host Management** > **Hosts** in the navigation pane.
#. On the **CCE Clusters** tab page, select the target CCE cluster and disable **Output to AOM**.
#. Click **OK**. After ICAgent is restarted, CCE standard output to AOM is disabled.
