:original_name: lts_05_0005.html

.. _lts_05_0005:

Log Search
==========

Follow the directions below to search logs by keyword and time range:

#. On the LTS console, choose **Log Management** in the navigation pane on the left.

#. In the log group list, click |image1| on the left of a log group name.

#. In the log stream list, click a log stream name.

#. In the upper right corner, select a time range. The default time range is 1 hour (from now).

   There are three types of time range: relative time from now, relative time from last, and specified time. Select a time range as required.

   .. note::

      -  From now: queries log data generated in a time range that ends with the current time, such as the previous 1, 5, or 15 minutes. For example, if the current time is 19:20:31 and 1 hour is selected as the relative time from now, the charts on the dashboard display the log data that is generated from 18:20:31 to 19:20:31.
      -  From last: queries log data generated in a time range that ends with the current time, such as the previous 1 or 15 minutes. For example, if the current time is 19:20:31 and 1 hour is selected as the relative time from last, the charts on the dashboard display the log data that is generated from 18:00:00 to 19:00:00.
      -  Specified time: queries log data that is generated in a specified time range.

#. On the log stream details page, you can search for logs using the following methods:

   a. In the search area, click in the search box. The drop-down list contains the following items:

      -  Structured fields or index fields: Built-in fields are not displayed in the drop-down list. However, when you enter a built-in field, the drop-down list is automatically associated and matched with the field.
      -  **NOT**, **AND**, **OR**, **:**, and **:\*** keywords can be displayed. Keywords other than **NOT** are displayed in the drop-down list only after you enter the keyword in the search box.

         .. note::

            -  When entering a keyword, you can press **Tab** to automatically add the first keyword displayed in the drop-down list.
            -  Keywords are case-insensitive.

      -  Historical records: A maximum of 20 historical records can be retained, but only the latest three records are displayed in the drop-down list.
      -  Quick search: quick search fields that have been created.
      -  Search syntax: common search syntax.

      Enter a keyword, or select a field and keyword from the drop-down list, and click **Query**.

      Logs that contain the keyword are displayed.

      .. note::

         -  Built-in fields include **appName**, **category**, **clusterId**, **clusterName**, **collectTime**, **containerName**, **hostIP**, **hostIPv6**, **hostId**, **hostName**, **nameSpace**, **pathFile**, **podName** and **serviceID**. By default, the fields are displayed in simplified mode, and **hostIP**, **hostName**, and **pathFile** are displayed at the beginning.
         -  The structured fields are displayed in **key:value** format.

   b. On the **Raw Logs** page, click a field in blue in the log content. You can select **Copy**, **Add To Search**, and **Exclude from Search** from the displayed drop-down list.

   c. Click a field for which quick analysis has been created to add it to the search box.

      .. note::

         If the field you click already exists in the search box, it will be replaced by this newly added one. If the field is added for the first time, fields in the search box are searched using the AND operator.

   d. In the search area, press the up and down arrows on the keyboard to select a keyword or search syntax from the drop-down list, press **Tab** or **Enter** to select a keyword or syntax, and click **Query**.

Common Log Search Operations
----------------------------

Log search operations include sharing logs and refreshing logs.

.. table:: **Table 1** Common operations

   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Operation                         | Description                                                                                                                                                                                                                                        |
   +===================================+====================================================================================================================================================================================================================================================+
   | Creating quick search criteria    | Click |image2| to create a quick search.                                                                                                                                                                                                           |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Sharing logs                      | Click |image3| to copy the link of the current log search page to share the logs that you have searched.                                                                                                                                           |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Refreshing logs                   | You can click |image4| to refresh logs in two modes: manual refresh and automatic refresh.                                                                                                                                                         |
   |                                   |                                                                                                                                                                                                                                                    |
   |                                   | -  Manual refresh: Select **Refresh Now** from the drop-down list.                                                                                                                                                                                 |
   |                                   | -  Automatic refresh: Select an interval from the drop-down list to automatically refresh logs. The interval can be 15 seconds, 30 seconds, 1 minute, or 5 minutes.                                                                                |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Copying logs                      | Click |image5| to copy the log content.                                                                                                                                                                                                            |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Viewing context of a log          | Click |image6| to view the log context.                                                                                                                                                                                                            |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Simplifying field details         | Click |image7| to view the simplified field details.                                                                                                                                                                                               |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Unfold/Fold                       | Click |image8| to display the full log content.                                                                                                                                                                                                    |
   |                                   |                                                                                                                                                                                                                                                    |
   |                                   | .. note::                                                                                                                                                                                                                                          |
   |                                   |                                                                                                                                                                                                                                                    |
   |                                   |    **Unfold** is enabled by default.                                                                                                                                                                                                               |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Downloading logs                  | Click |image9|. On the displayed **Download Logs** page, click **Direct Download** or **Transfer and Download**.                                                                                                                                   |
   |                                   |                                                                                                                                                                                                                                                    |
   |                                   | **Direct Download**: Download log files to the local PC. Up to 5000 logs can be downloaded at a time.                                                                                                                                              |
   |                                   |                                                                                                                                                                                                                                                    |
   |                                   | Select **.csv** or **.txt** from the drop-down list and click **Download** to export logs to the local PC.                                                                                                                                         |
   |                                   |                                                                                                                                                                                                                                                    |
   |                                   | .. note::                                                                                                                                                                                                                                          |
   |                                   |                                                                                                                                                                                                                                                    |
   |                                   |    -  If you select **Export .csv**, logs are exported as a table.                                                                                                                                                                                 |
   |                                   |    -  If you select **Export .txt**, logs are exported as a **.txt** file.                                                                                                                                                                         |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Layout                            | Move the cursor over |image10| and choose **Layout** from the drop-down list. On the displayed **Layout** page, specify whether to simplify field display and show fields.                                                                         |
   |                                   |                                                                                                                                                                                                                                                    |
   |                                   | -  **Simple View**: If this is enabled, the fields are displayed in a simplified manner.                                                                                                                                                           |
   |                                   | -  **Show/Hide**: When the visibility of a field is disabled, the field is not displayed in the log content.                                                                                                                                       |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | JSON                              | Move the cursor over |image11|, click **JSON**, and set JSON formatting.                                                                                                                                                                           |
   |                                   |                                                                                                                                                                                                                                                    |
   |                                   | .. note::                                                                                                                                                                                                                                          |
   |                                   |                                                                                                                                                                                                                                                    |
   |                                   |    Formatting is enabled by default. The default number of expanded levels is 2.                                                                                                                                                                   |
   |                                   |                                                                                                                                                                                                                                                    |
   |                                   | -  Formatting enabled: Set the default number of expanded levels. Maximum value: **10**.                                                                                                                                                           |
   |                                   | -  Formatting disabled: JSON logs will not be formatted for display.                                                                                                                                                                               |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Invisible fields (|image12|)      | This list displays the invisible fields configured in the layout settings.                                                                                                                                                                         |
   |                                   |                                                                                                                                                                                                                                                    |
   |                                   | -  The |image13| button is unavailable for log streams without layout settings configured.                                                                                                                                                         |
   |                                   | -  If the log content is **CONFIG_FILE** and layout settings are not configured, the default invisible fields include **appName**, **clusterId**, **clusterName**, **containerName**, **hostIPv6**, **NameSpace**, **podName**, and **serviceID**. |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Search Syntax and Examples
--------------------------

**Search syntax:**

.. table:: **Table 2** Search syntax

   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Filter                            | Description                                                                                                                                                                             |
   +===================================+=========================================================================================================================================================================================+
   | Exact search by keyword           | LTS searches for logs containing the exact keyword (case-sensitive) that you specify. A keyword is the word between two adjacent delimiters.                                            |
   |                                   |                                                                                                                                                                                         |
   |                                   | You can add an asterisk (``*``) after a keyword, for example, **error\***, if you are not familiar with delimiters.                                                                     |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Exact search by phrase            | LTS searches for logs containing the exact phrase (case-sensitive) that you specify.                                                                                                    |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | &&                                | Intersection of search results                                                                                                                                                          |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | \|\|                              | Union of search results                                                                                                                                                                 |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | AND                               | Intersection of search results                                                                                                                                                          |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | and                               | Intersection of search results                                                                                                                                                          |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OR                                | Union of search results                                                                                                                                                                 |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | or                                | Union of search results                                                                                                                                                                 |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | NOT                               | Logs that contain the keyword after **NOT** are excluded.                                                                                                                               |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | not                               | Logs that contain the keyword after **not** are excluded.                                                                                                                               |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ?                                 | Fuzzy search. The question mark (?) can be put in the middle or at the end of a keyword to replace a character.                                                                         |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | >                                 | Search for structured long or float fields with values greater than a specified number. For example, **num > 10**.                                                                      |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | <                                 | Search for structured long or float fields with values less than a specified number. For example, **num < 10**.                                                                         |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | =                                 | Search for structured long or float fields with values equal to a specified number. For example, **num = 10**.                                                                          |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | >=                                | Search for structured long or float fields with values greater than or equal to a specified number. For example, **num >= 10**.                                                         |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | <=                                | Search for structured long or float fields with values less than or equal to a specified number. For example, **num <= 10**.                                                            |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :                                 | Search for a specified field (key:value). For example, **request_method:GET**.                                                                                                          |
   |                                   |                                                                                                                                                                                         |
   |                                   | Use double quotation marks ("") to enclose a field name or value that contains reserved characters, such as spaces and colons (:). For example, **"file info":apsara**.                 |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ""                                | Enclose a syntax keyword to convert it into common characters. For example, **"and"**.                                                                                                  |
   |                                   |                                                                                                                                                                                         |
   |                                   | This "and" means searching for logs that contain this word. It is not an operator.                                                                                                      |
   |                                   |                                                                                                                                                                                         |
   |                                   | All words enclosed in double quotation marks ("") are considered as a whole.                                                                                                            |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | \\                                | Escape double quotation marks (""). The escaped quotation marks indicate the symbol itself. For example, to search for **instance_id:nginx"01"**, use **instance_id:nginx\\"01\\"**.    |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | \*                                | An asterisk (``*``) can be placed only after the keyword and can match zero, one, or multiple characters. For example, **host:abcd*c**.                                                 |
   |                                   |                                                                                                                                                                                         |
   |                                   | .. note::                                                                                                                                                                               |
   |                                   |                                                                                                                                                                                         |
   |                                   |    LTS will find 100 words that meet the search criteria in all logs and return these logs.                                                                                             |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | in                                | Query logs whose field values are in a specified range. Brackets indicate a closed interval, and parentheses indicate an open interval. Numbers are separated with spaces. Example:     |
   |                                   |                                                                                                                                                                                         |
   |                                   | **request_time in [100 200]** and **request_time in (100 200]**                                                                                                                         |
   |                                   |                                                                                                                                                                                         |
   |                                   | .. note::                                                                                                                                                                               |
   |                                   |                                                                                                                                                                                         |
   |                                   |    Enter **in** in lowercase and use only long or float fields.                                                                                                                         |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ()                                | Specify fields that should be matched with higher priority. Use **and**, **or**, and **not** to connect fields. Example: **(request_method:GET or request_method:POST) and status:200** |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | key:#"abc def"                    | Search for specified field names and values (key:value) after field indexing is configured.                                                                                             |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | #"abc def"                        | Full text search. LTS splits an entire log into multiple words based on the delimiter you set. Search for logs using specified keywords (field name and value) and rules.               |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. note::

   Operators (such as **&&**, **\|\|**, **AND**, **OR**, **NOT**, **\***, **?**, **:**, **>**, **<**, **=**, **>=**, and **<=**) contained in raw logs cannot be used to search for logs.

**Search rules:**

-  Fuzzy search is supported.

   For example, if you enter **error\***, all logs containing **error** will be displayed and those start with **error** will be highlighted.

-  You can use a combination of multiple search criteria in the key and value format: *key1:value1* **AND** *key2:value2* or *key1:value1* **OR** *key2:value2*. After entering or selecting *key1:value1*, you need to add **AND** or **OR** before entering or selecting *key2:value2* in the search box.

-  Click a keyword and select one of the three operations from the displayed drop-down list: **Copy**, **Add To Search**, and **Exclude from Search**.

   **Copy**: Copy the field.

   **Add To Search**: Add **AND** *field: value* to the search statement.

   **Exclude from Search**: Add **NOT** *field: value* to the query statement.

**Searching sample**

-  Search for logs containing **start**: Enter **start**.
-  Search for logs containing **start to refresh**: Enter **start to refresh**.
-  Search for the logs containing both keyword **start** and **unexpected**: Enter **start && unexpected**.
-  Search for logs containing both **start** and **unexpected**: Enter **start AND unexpected**.
-  Search for the logs containing keyword **start** or **unexpected**: Enter **start \|\| unexpected**.

-  Search for logs containing **start** or **unexpected**: Enter **start OR unexpected**.
-  Logs that do not contain *query1*: **NOT content:** *query1*.
-  **error\***: logs that contain **error**.
-  **er?or**: logs that start with **er**, is followed by any single character, and end with **or**.
-  If your keyword contains a colon (:), use the **content:** *Keyword* format. Example: **content: "120.46.138.115:80"** or **content: 120.46.138.115:80**.
-  *query1* **AND** *query2* **AND NOT content:** *query3*: logs that contain both *query1* and *query2* but not *query3*.

.. note::

   -  When you enter a keyword to query logs, the keyword is case-sensitive. Log contents you queried are case-sensitive but the highlighted log contents are case-sensitive.
   -  The asterisk (*) and question mark (?) do not match special characters such as hyphens (-) and spaces.
   -  For fuzzy match, the question mark (?) or asterisk (*) can only go in the middle or at the end of a keyword. For example, you can enter **ER?OR** or **ER*R**.
   -  When you search logs by keyword, if a single log contains more than 255 characters, exact search may fail.

.. |image1| image:: /_static/images/en-us_image_0000001463823649.png
.. |image2| image:: /_static/images/en-us_image_0000001561940610.png
.. |image3| image:: /_static/images/en-us_image_0000001421609924.png
.. |image4| image:: /_static/images/en-us_image_0000001481236306.png
.. |image5| image:: /_static/images/en-us_image_0000001262546024.png
.. |image6| image:: /_static/images/en-us_image_0000001262546228.png
.. |image7| image:: /_static/images/en-us_image_0000001611750029.png
.. |image8| image:: /_static/images/en-us_image_0000001576175974.png
.. |image9| image:: /_static/images/en-us_image_0000001474530441.png
.. |image10| image:: /_static/images/en-us_image_0000001476964177.png
.. |image11| image:: /_static/images/en-us_image_0000001410398388.png
.. |image12| image:: /_static/images/en-us_image_0000001316788136.png
.. |image13| image:: /_static/images/en-us_image_0000001320576858.png
