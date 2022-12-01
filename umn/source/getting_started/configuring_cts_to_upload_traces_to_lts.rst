:original_name: lts_01_0010.html

.. _lts_01_0010:

Configuring CTS to Upload Traces to LTS
=======================================

Scenarios
---------

This section describes how to enable trace analysis on the Cloud Trace Service (CTS) console to report traces to LTS, so you can query the traces on the LTS console.

Operation process
-----------------

.. _lts_01_0010__en-us_topic_0224007630_fig1610211279519:

.. figure:: /_static/images/en-us_image_0224007675.png
   :alt: **Figure 1** Flowchart

   **Figure 1** Flowchart

Operations in :ref:`Figure 1 <lts_01_0010__en-us_topic_0224007630_fig1610211279519>` are performed on different consoles:

#. CTS console: Enabling CTS and creating and configuring a tracker

2. LTS console: Viewing traces reported by CTS

Enabling CTS
------------

You can perform the following operations to enable CTS and create a tracker.

#. Log in to the management console.

#. In the upper left corner of the management console, select the target region and project.

#. Click **Service List** and choose **Management & Deployment** > **Cloud Trace Service**.

#. In the navigation pane on the left, choose **Tracker**.

#. On the **Tracker** page, click **Enable CTS**.

#. On the displayed page, set **OBS Bucket**.


   .. figure:: /_static/images/en-us_image_0224007681.png
      :alt: **Figure 2** Enabling CTS

      **Figure 2** Enabling CTS

#. Click **OK**.

   After you enable CTS, tracker **system** is automatically created. All recorded traces are associated with the tracker.

   Currently, only one tracker can be created for each account.

Configuring the Tracker
-----------------------

You can perform the following operations to enable the trace analysis function, thus reporting CTS traces to LTS.

#. On the **Tracker** page, click **Configure** in the **Operation** column.

   The **Configure Tracker** page is displayed.

#. On the displayed page, enable **Trace Analysis**.


   .. figure:: /_static/images/en-us_image_0224007684.png
      :alt: **Figure 3** Configuring a tracker

      **Figure 3** Configuring a tracker

   .. note::

      During CTS trace reporting, the system automatically creates a log group and a log topic on the LTS console.

#. Click **OK**.

Viewing Logs in Real Time
-------------------------

You can perform the following operations to view logs reported by CTS:

#. Click **Service List** and choose **Management & Deployment** > **Log Tank Service**.

#. In the log group list, click the name of the target log group.

#. In the log topic list, locate the target log topic and click **View** in the **Operation** column.


   .. figure:: /_static/images/en-us_image_0224007615.png
      :alt: **Figure 4** Viewing logs in real time

      **Figure 4** Viewing logs in real time

   Logs are reported to LTS every 10 minutes. In the log display area, you may wait for at most 10 minutes to view the logs.

   In addition, you can customize log display by clicking **Clear**, **Pause**, or **Close** in the upper right corner.


   .. figure:: /_static/images/en-us_image_0224007642.png
      :alt: **Figure 5** Log display area

      **Figure 5** Log display area

   -  **Clear**: clears all logs that are displayed in the log display area.

   -  **Pause**: pauses the real-time log display so that you can view details of the displayed logs.

      After you click **Pause**, the button changes to **Continue**. You can click **Continue** to resume the log display.

   -  **Close**: closes the real-time log view page. You are redirected to the **Log Topic List** page.
