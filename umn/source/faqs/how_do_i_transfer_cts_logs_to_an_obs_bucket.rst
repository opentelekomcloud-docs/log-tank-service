:original_name: lts_faq_0610.html

.. _lts_faq_0610:

How Do I Transfer CTS Logs to an OBS Bucket?
============================================

When Cloud Trace Service (CTS) is connected to LTS, a log group and log stream are automatically created for CTS on the LTS console. To transfer CTS logs to OBS, do as follows:

#. Log in to the CTS console and choose **Tracker List** in the navigation pane on the left.

#. Click **Configure** on the row of the **system** tracker.

#. Click **Next** to enable **Transfer to LTS**.

#. Access the LTS console, choose **Log Transfer** in the navigation pane on the left, and click **Configure Log Transfer** in the upper right corner.

   Set **Log Group Name** to **CTS** and **Log Stream Name** to **system-trace**. Specify other parameters and click **OK** to transfer CTS logs to the selected OBS bucket.

#. View the transferred CTS logs in the specified OBS bucket on the OBS console.
