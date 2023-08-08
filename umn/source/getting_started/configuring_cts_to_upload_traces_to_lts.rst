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

Follow the directions below to enable transfer to LTS so traces can be reported to LTS:

#. On the **Tracker** page, click **Configure** in the **Operation** column.

   The **Configure Tracker** page is displayed.

#. Enable **Transfer to LTS**.


   .. figure:: /_static/images/en-us_image_0000001427369668.png
      :alt: **Figure 3** Configuring a tracker

      **Figure 3** Configuring a tracker

   .. note::

      A log group and a log stream will be created automatically for the reported traces on the LTS console.

#. Click **Next** to preview the created tracker.

#. Click **Configure**.

Viewing Logs in Real Time
-------------------------

You can perform the following operations to view logs reported by CTS:

#. Click **Service List** and choose **Management & Deployment** > **Log Tank Service**.

#. In the log group list, click |image1| on the left of a log group name. The log stream list is displayed.

#. Click Log Stream to go to the log details and view real-time logs.


   .. figure:: /_static/images/en-us_image_0000001424778604.png
      :alt: **Figure 4** Viewing logs in real time

      **Figure 4** Viewing logs in real time

   Logs are reported to LTS once every five seconds. You may wait for at most five seconds before the logs are displayed.

   You can control log display by clicking **Clear** or **Pause** in the upper right corner.

   -  **Clear**: clears all logs that are displayed in the log display area.

   -  **Pause**: pauses the real-time log display so that you can view details of the displayed logs.

      After you click **Pause**, the button changes to **Continue**. You can click **Continue** to resume the log display.

.. |image1| image:: /_static/images/en-us_image_0000001424625748.png
