:original_name: lts_faq_0610.html

.. _lts_faq_0610:

How Do I Transfer CTS Logs to an OBS Bucket?
============================================

When Cloud Trace Service (CTS) is connected to LTS, a log group and log stream are automatically created for CTS on the LTS console. To transfer CTS logs to OBS, do as follows:

#. Log in to the CTS console and choose **Tracker List** in the navigation pane.

#. Click **Configure** in the row of the tracker **system**.

#. On the **Basic Information** page, click **Next**.

#. In the **Configure Transfer** step, configure parameters of log transfer to OBS, enable **Transfer to LTS**, and click **Next**.

#. Confirm the configurations and click **Configure**.

#. Access the LTS console, choose **Log Transfer** in the navigation pane on the left, and click **Configure Log Transfer** in the upper right corner.

   Set **Log Group Name** to **CTS** and **Log Stream Name** to **system-trace**. Specify other parameters and click **OK** to transfer CTS logs to the selected OBS bucket.

#. View the transferred CTS logs in the specified OBS bucket on the OBS console.
