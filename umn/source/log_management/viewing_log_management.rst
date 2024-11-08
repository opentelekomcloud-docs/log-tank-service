:original_name: lts_04_1154.html

.. _lts_04_1154:

Viewing Log Management
======================

The log management page displays resource statistics, your favorite log streams/favorite log streams (local cache), alarm statistics, latest alarms, and recently viewed log streams.

Resource Statistics
-------------------

The **Statistics** area shows resource statistics and details by category in charts. The statistics are for reference only.

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**. The **Log Management** page is displayed by default.

#. Under **Overview**, click **Details** in the upper right corner of the **Statistics** area to access the resource statistics details page.

#. Select a time range as required. By default, resource statistics display log resource data of one week (from now).

   There are three types of time range: relative time from now, relative time from last, and specified time.

   .. note::

      -  **From now**: queries log data generated in a time range that ends with the current time, such as the previous 1, 5, or 15 minutes. For example, if the current time is 19:20:31 and **1 hour** is selected as the relative time from now, the charts on the dashboard display the log data that is generated from 18:20:31 to 19:20:31.
      -  **From last**: queries log data generated in a time range that ends with the current time, such as the previous 1 or 15 minutes. For example, if the current time is 19:20:31 and **1 hour** is selected as the relative time from last, the charts on the dashboard display the log data that is generated from 18:00:00 to 19:00:00.
      -  **Specified**: queries log data that is generated in a specified time range.

#. View the resource statistics.

   -  **Read/Write**: LTS charges for the amount of compressed log data read from and written to LTS. Generally, the log compression ratio is 5:1.
   -  **Index Traffic**: Raw logs are full-text indexed (delimited) by default for log search.
   -  **Log**: Space used for storing compressed logs, indexes, and copies is billed. The space is roughly the size of the raw logs.
   -  **Raw Log Traffic**: size of raw logs.

#. View the resource statistics of **Log Groups (Top 100)** and **Log Streams (Top 100)**. You can select a time range and view the daily standard storage volume (GB), daily index traffic (GB), and daily read/write traffic (GB) in a table or bar chart based on the selected time range.

   -  For a new log group or log stream, resource statistics will be collected in at least one hour.
   -  Click the name of one of the top 100 log groups to query its log stream resource statistics.
   -  Click |image1| to download the resource statistics of the log groups and streams.

      .. note::

         The downloaded files are in **.CSV** format.

Alarm Statistics and Latest Alarms
----------------------------------

In the lower part of **Overview**, you can view alarm statistics and latest alarms.

-  The **Alarms** area displays the total number of LTS alarms and the number of alarms of each severity (**Critical**, **Major**, **Minor**, and **Warning**). You can view alarm statistics of the last 30 minutes, last 1 hour, last 6 hours, last 1 day, or last 1 week.
-  The **Latest Alarms** area displays a maximum of three latest alarm rules in the last 30 minutes. To view more alarms or add alarm rules, click |image2|.

Log Groups
----------

Log groups and log streams are listed in **Log Groups**. For more information, see :ref:`Managing Log Groups <lts_04_0003>` and :ref:`Managing Log Streams <lts_04_0004>`.

My Favorites/My Favorites (Local Cache)
---------------------------------------

This area displays the log streams you have added to favorites, including **My Favorites** and **My Favorites(Local Cache)**.

-  **My Favorites**: Save log streams to the database. This function is disabled by default. If your account has the write permission, **My Favorites** and **My Favorites(Local Cache)** are displayed.
-  **My Favorites(Local Cache)**: Save log streams to the local cache of the browser. This function is disabled by default. This parameter is displayed for both writable and read-only users.

   .. note::

      If your account has the write permission, at least one of **My Favorites** and **My Favorites(Local Cache)** is enabled. Otherwise, log streams cannot be added to favorites.

Adding frequently used log streams to your favorites helps you quickly locate them.

The following example shows how to add a log stream of log group **lts-test** to favorites:

#. In the **Log Groups** list, click |image3| on the left of log group **lts-test**.
#. Click |image4| in the **Operation** column of the target log stream. On the displayed dialog box, enable **My Favorites** and/or **My Favorites(Local Cache)** and click **OK**.

   .. note::

      You can remove a favorite in either of the following ways:

      -  In the log stream list, click |image5| in the row of the log stream.
      -  In the **My Favorites** area, hover the cursor over the log stream and click |image6|.

#. After the log stream is added to favorites, it is displayed in **My Favorites**/**My Favorites(Local Cache)** on the right.

Recently Visited
----------------

This area displays a maximum of three log streams that are recently visited.


.. figure:: /_static/images/en-us_image_0000001924750594.png
   :alt: **Figure 1** Recently visited

   **Figure 1** Recently visited

FAQ
---

This area displays frequently asked questions.

.. |image1| image:: /_static/images/en-us_image_0000001966867180.png
.. |image2| image:: /_static/images/en-us_image_0000001924745402.png
.. |image3| image:: /_static/images/en-us_image_0000001924750582.png
.. |image4| image:: /_static/images/en-us_image_0000001952029417.png
.. |image5| image:: /_static/images/en-us_image_0000001952029421.png
.. |image6| image:: /_static/images/en-us_image_0000001951869649.png
