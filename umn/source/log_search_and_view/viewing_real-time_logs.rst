:original_name: lts_05_0006.html

.. _lts_05_0006:

Viewing Real-Time Logs
======================

You can view reported logs on the LTS console in real time.

Prerequisites
-------------

-  You have created log groups and log streams.
-  You have installed :ref:`ICAgent <lts_02_0013>`.
-  You have configured log collection rules.

Procedure
---------

#. On the LTS console, click **Log Management**.
#. In the log group list, click |image1| on the left of a log group name.
#. In the log stream list, click a log stream name. The log stream details page is displayed.
#. On the log stream details page, click the **Real-Time Logs** tab to view logs in real time.

Logs are reported to LTS once every minute. You may wait for at most 1 minute before the logs are displayed.

In addition, you can customize log display by clicking **Clear** or **Pause** in the upper right corner.

-  **Clear**: Displayed logs will be cleared from the real-time view.

-  **Pause**: Loading of new logs to the real-time view will be paused.

   After you click **Pause**, the button changes to **Continue**. You can click **Continue** to resume the log loading to the real-time view.

.. note::

   Stay on the **Real-Time Logs** tab to keep updating them in real time. If you leave the **Real-Time Logs** tab page, logs will stop being loaded in real time. The next time you access the tab, the logs that were shown before you left the tab will not be displayed.

.. |image1| image:: /_static/images/en-us_image_0000001413544114.png
