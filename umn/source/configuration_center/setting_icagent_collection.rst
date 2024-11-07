:original_name: lts_05_0003.html

.. _lts_05_0003:

Setting ICAgent Collection
==========================

On the **ICAgent Collection** tab page, you can disable or enable ICAgent collection (that is, specify whether ICAgent collects log data), syslog log collection to AOM, and container standard output to AOM.

Setting Collection
------------------

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**.

#. In the navigation pane, choose **Configuration Center**. Click the **ICAgent Collection** tab.

#. Toggle the **ICAgent Collection** switch to control whether ICAgent collects logs.

   -  **ICAgent Collection** is toggled on by default. If you do not need to collect logs, toggle it off to reduce resource usage.
   -  After it is toggled off, ICAgent will stop collecting logs, and the log collection function on the AOM console will also be disabled.


   .. figure:: /_static/images/en-us_image_0000001965754048.png
      :alt: **Figure 1** Enabling or disabling log collection

      **Figure 1** Enabling or disabling log collection

#. Toggle the **Collect Syslog Logs to AOM** switch to set whether ICAgent collects Syslogs to AOM 1.0. If it is toggled off, ICAgent does not collect Syslog logs to AOM 1.0. This function is only available with ICAgent 5.12.182 and later.

#. **Output to AOM**: Select a CCE cluster and toggle on or off the **Apply to Cluster** switch for it. If it is toggled off, ICAgent does not collect the cluster stdout logs to AOM. This function is only available with ICAgent 5.12.133 and later. You are advised to collect container standard output to LTS instead of AOM. For details, see :ref:`Ingesting CCE Application Logs to LTS <lts_04_0511>`.
