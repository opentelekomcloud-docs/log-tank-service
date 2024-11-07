:original_name: lts_0904.html

.. _lts_0904:

Setting LTS Log Collection Quota
================================

Enabling or Disabling Log Collection Beyond Free Quota
------------------------------------------------------

When the monthly free quota (500 MB) is used up, you will be billed for any excess usage on a pay-per-use basis. To avoid extra expenses, you can configure log collection to stop when the quota runs out.

.. note::

   -  If this function is enabled, logs will continue to be collected after the free quota (500 MB) is used up. You will be billed for the excess usage on a pay-per-use basis.
   -  Log usage, including log read/write, log indexing, and log retention, are billed in LTS. If log collection is disabled when the free quota is used up, no fee is generated for log read/write and indexing because these operations will not be performed. However, log data that beyond the free quota is still retained in LTS and fees are generated for the log retention. When the logs age out after the specified retention period, no fees will be generated.
   -  If you enable or disable **Continue to Collect Logs When the Free Quota is Exceeded** in AOM, this function will be synchronously enabled or disabled in LTS.

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**.

#. In the navigation pane, choose **Configuration Center**. The **Quota Configuration** tab page is displayed by default.

#. Disable **Continue to Collect Logs When the Free Quota Is Exceeded**.

   When the free quota (500 MB) is used up, log collection will be suspended.
