:original_name: lts_04_0008.html

.. _lts_04_0008:

Viewing Real-Time Logs
======================

You can view the logs reported to the LTS console in real time.

Prerequisites
-------------

-  You have created log groups and log streams.
-  You have installed :ref:`ICAgent <lts_02_0013>`.
-  You have configured log collection rules.

Procedure
---------

#. Log in to the LTS console and choose **Log Management**.
#. In the log group list, click the name of a log group.
#. In the log stream list, click the name of a log stream.
#. On the log stream details page, click the **Real-Time Logs** tab to view logs in real time.

Logs are reported to LTS once every five seconds. You may wait for at most five seconds before the logs are displayed.

You can control log display by clicking **Clear** or **Pause** in the upper right corner.

-  **Clear**: Displayed logs will be cleared from the real-time view.

-  **Pause**: Loading of new logs to the real-time view will be paused.

   After you click **Pause**, the button changes to **Continue**. You can click **Continue** to resume the log loading to the real-time view.

.. note::

   Stay on the **Real-Time Logs** tab to keep updating them in real time. If you leave the **Real-Time Logs** tab page, logs will stop being loaded in real time. The next time you access the tab, the logs that were shown before you left the tab will not be displayed.
