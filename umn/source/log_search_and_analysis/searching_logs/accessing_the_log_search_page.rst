:original_name: lts_05_0005.html

.. _lts_05_0005:

Accessing the Log Search Page
=============================

After configuring log structuring parsing and indexing, you can enter statements to search for log records that contain specific keywords. You can also search for log data by time range to locate events and issues that occur in a specified period.

Search statements are used to define the filter criteria for log query and obtain the logs that meet the criteria. A search statement may be a keyword, a value, a value range, a space, an asterisk (``*``), or the like. If it is a space or asterisk (``*``), no filtering criteria is specified. For more information, see :ref:`Using LTS Search Syntax <lts_05_0111>`.

Searching Logs
--------------

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**.

#. On the **Log Management** page, click the target log group or stream to access the log stream details page.

#. On the **Log Search** tab page, select a time range from the drop-down list to view log data accordingly.

   There are three types of time range: relative time from now, relative time from last, and specified time. Select a time range as required.

   -  **From now**: queries log data generated in a time range that ends with the current time, such as the previous 1, 5, or 15 minutes. For example, if the current time is 19:20:31 and **1 hour** is selected as the relative time from now, the charts on the dashboard display the log data that is generated from 18:20:31 to 19:20:31.
   -  **From last**: queries log data generated in a time range that ends with the current time, such as the previous 1 or 15 minutes. For example, if the current time is 19:20:31 and **1 hour** is selected as the relative time from last, the charts on the dashboard display the log data that is generated from 18:00:00 to 19:00:00.
   -  **Specified**: queries log data that is generated in a specified time range.

#. Enter search criteria in the search box based on :ref:`Using LTS Search Syntax <lts_05_0111>` to view, search for, and filter log data.

   a. In the search area, click the search box, enter a keyword or select a field or keyword from the drop-down list, and click **Search**.

      -  The structured fields are displayed in **key:value** format.

   b. In the search area, press the up and down arrows on the keyboard to select a keyword or search syntax from the drop-down list, press **Tab** or **Enter** to select a keyword or syntax, and click **Search**.

   c. Click a field for which quick analysis has been enabled to add it to the search box. For details about how to enable quick analysis, see :ref:`Creating an LTS Quick Analysis Task <lts_05_0007>`.

      If the field you click already exists in the search box, it will be replaced by this newly added one. If the field is added for the first time, fields in the search box are searched using the AND operator.

#. On the **Log Search** tab page, perform the following operations. For more operations, see :ref:`Common Log Search Operations <lts_05_0005__en-us_topic_0000001252577734_section36611942194013>`.

   a. Under **Log Statistics**, view the bar chart showing the log quantity in different time segments. The scale of the log quantity is displayed on the left.
   b. In the log content area, hover the cursor over a field and click the log content in blue. You can search for logs by copying, adding to query, and excluding from query.
   c. In the log content area, you can select a list or raw log to display its log content.

#. Set the layout of log data, including whether to display fields or display fields in a simple view.

   a. Select **Edit layouts** from the layout drop-down list to access the layout setting page. The list also contains options such as the default layout, pure layout, and default container log layout, for you to set whether to display fields.

      -  **Cloud**: This mode is applicable to users who have the write permission. Layout information is stored on the cloud.
      -  **Local Cache**: This mode is applicable to users who have only the read permission. Layout information is cached in the local browser.

   b. Click |image1| to add a custom layout and set the layout name and visibility of layout fields.
   c. After the setting is complete, click **OK**. The new custom layout is displayed in the drop-down list.

.. _lts_05_0005__en-us_topic_0000001252577734_section36611942194013:

Common Log Search Operations
----------------------------

In the log content display area, you can share and download logs, and view context. For details, see :ref:`Table 1 <lts_05_0005__en-us_topic_0000001252577734_table755214580176>`.

.. _lts_05_0005__en-us_topic_0000001252577734_table755214580176:

.. table:: **Table 1** Common operations

   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Operation                         | Description                                                                                                                                                                                                                                                                  |
   +===================================+==============================================================================================================================================================================================================================================================================+
   | Interactive search                | Click **Interactive Mode** in front of the search box. In the displayed **Interactive Search** dialog box, select fields for index configuration, set the filtering mode, and add associations and groups. After the setting is complete, you can preview the search syntax. |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Creating quick search             | Click |image2| to create a quick search.                                                                                                                                                                                                                                     |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Sharing logs                      | Click |image3| to copy the link of the current log search page to share the logs that you have searched.                                                                                                                                                                     |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Refreshing logs                   | You can click |image4| to refresh logs in two modes: manual refresh and automatic refresh.                                                                                                                                                                                   |
   |                                   |                                                                                                                                                                                                                                                                              |
   |                                   | -  Manual refresh: Select **Refresh Now** from the drop-down list.                                                                                                                                                                                                           |
   |                                   | -  Automatic refresh: Select an interval from the drop-down list to automatically refresh logs. The interval can be 15 seconds, 30 seconds, 1 minute, or 5 minutes.                                                                                                          |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Copying logs                      | Click |image5| to copy the log content.                                                                                                                                                                                                                                      |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Viewing context of a log          | Click |image6| to view the log context.                                                                                                                                                                                                                                      |
   |                                   |                                                                                                                                                                                                                                                                              |
   |                                   | You can select **Simple View** to view the log context. You can also download the context.                                                                                                                                                                                   |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | More operations                   | Click |image7| to access the log details page of the time segment and view more log information.                                                                                                                                                                             |
   |                                   |                                                                                                                                                                                                                                                                              |
   |                                   | -  On the **Extended Fields** tab page, view field names and values. You can also click buttons in the **Operation** column to add a field to or exclude a field from a query, set whether a field exists or does not exist, or set whether a field is hidden.               |
   |                                   | -  On the **JSON Format** tab page, view the JSON format of logs.                                                                                                                                                                                                            |
   |                                   | -  On the **Context Logs** tab page, you can set the number of lines to be queried and filtered fields. You can also download logs and enable the summary mode.                                                                                                              |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Unfold/Fold                       | Click |image8| to display all the log content. This unfold button is enabled by default. Click |image9| to fold the log content.                                                                                                                                             |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Downloading logs                  | Click |image10|. On the displayed **Download Logs** page, click **Direct Download** or **Transfer and Download**.                                                                                                                                                            |
   |                                   |                                                                                                                                                                                                                                                                              |
   |                                   | **Direct Download**: Download log files to the local PC. Up to 5,000 logs can be downloaded at a time.                                                                                                                                                                       |
   |                                   |                                                                                                                                                                                                                                                                              |
   |                                   | Select **.csv** or **.txt** from the drop-down list and click **Download** to export logs to the local PC.                                                                                                                                                                   |
   |                                   |                                                                                                                                                                                                                                                                              |
   |                                   | .. note::                                                                                                                                                                                                                                                                    |
   |                                   |                                                                                                                                                                                                                                                                              |
   |                                   |    -  If you select **Export .csv**, logs are exported as a table.                                                                                                                                                                                                           |
   |                                   |    -  If you select **Export .txt**, logs are exported as a **.txt** file.                                                                                                                                                                                                   |
   |                                   |                                                                                                                                                                                                                                                                              |
   |                                   | **Transfer and Download**: Download log files through OBS transfer tasks. Up to 20 million logs can be downloaded at a time. Click **Transfer** to access the **Configure Log Transfer** page. For details, see :ref:`Transferring Logs to OBS <lts_04_0041>`.               |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Hiding/Expanding all              | Click |image11| to set the number of lines displayed in the log content. Click |image12| to hide the log content.                                                                                                                                                            |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | JSON                              | Move the cursor over |image13|, click **JSON**, and set JSON formatting.                                                                                                                                                                                                     |
   |                                   |                                                                                                                                                                                                                                                                              |
   |                                   | Formatting is enabled by default. The default number of expanded levels is 2.                                                                                                                                                                                                |
   |                                   |                                                                                                                                                                                                                                                                              |
   |                                   | -  Formatting enabled: Set the default number of expanded levels. Maximum value: **10**.                                                                                                                                                                                     |
   |                                   | -  Formatting disabled: JSON logs will not be formatted for display.                                                                                                                                                                                                         |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Collapse configuration            | Move the cursor over |image14|, click **Log Collapse**, and set the maximum characters to display in a log.                                                                                                                                                                  |
   |                                   |                                                                                                                                                                                                                                                                              |
   |                                   | If the number of characters in a log exceeds the maximum, the extra characters will be hidden. Click **Expand** to view all.                                                                                                                                                 |
   |                                   |                                                                                                                                                                                                                                                                              |
   |                                   | Logs are collapsed by default, with a default character limit of 400.                                                                                                                                                                                                        |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Log time display                  | Move the cursor over |image15| and click **Log Time Display**. On the page that is displayed, set whether to display milliseconds and whether to display the time zone. Milliseconds are displayed by default.                                                               |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Virtual Scrolling                 | Move the cursor over |image16| and click **Virtual Scrolling**. On the page that is displayed, set whether to enable virtual scrolling and enter the buffer size.                                                                                                            |
   |                                   |                                                                                                                                                                                                                                                                              |
   |                                   | -  Virtual scrolling eliminates or minimizes frame and page freezing for better user experience.                                                                                                                                                                             |
   |                                   | -  Data is re-rendered during the process. This may affect smoothness.                                                                                                                                                                                                       |
   |                                   | -  The buffer size determines the amount of data that can be loaded simultaneously. The larger the buffer, the more data loaded simultaneously, but the worse the scrolling performance.                                                                                     |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Invisible fields (|image17|)      | This list displays the invisible fields configured in the layout settings.                                                                                                                                                                                                   |
   |                                   |                                                                                                                                                                                                                                                                              |
   |                                   | -  The |image18| button is unavailable for log streams without layout settings configured.                                                                                                                                                                                   |
   |                                   | -  If the log content is **CONFIG_FILE** and layout settings are not configured, the default invisible fields include **appName**, **clusterId**, **clusterName**, **containerName**, **hostIPv6**, **NameSpace**, **podName**, and **serviceID**.                           |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001954290246.png
.. |image2| image:: /_static/images/en-us_image_0000001561940610.png
.. |image3| image:: /_static/images/en-us_image_0000001421609924.png
.. |image4| image:: /_static/images/en-us_image_0000001481236306.png
.. |image5| image:: /_static/images/en-us_image_0000001262546024.png
.. |image6| image:: /_static/images/en-us_image_0000001262546228.png
.. |image7| image:: /_static/images/en-us_image_0000002018849674.png
.. |image8| image:: /_static/images/en-us_image_0000001611940613.png
.. |image9| image:: /_static/images/en-us_image_0000001612061257.png
.. |image10| image:: /_static/images/en-us_image_0000001474530441.png
.. |image11| image:: /_static/images/en-us_image_0000001612024421.png
.. |image12| image:: /_static/images/en-us_image_0000001611907193.png
.. |image13| image:: /_static/images/en-us_image_0000001410398388.png
.. |image14| image:: /_static/images/en-us_image_0000001608069337.png
.. |image15| image:: /_static/images/en-us_image_0000001674961080.png
.. |image16| image:: /_static/images/en-us_image_0000001809715517.png
.. |image17| image:: /_static/images/en-us_image_0000001316788136.png
.. |image18| image:: /_static/images/en-us_image_0000001320576858.png
