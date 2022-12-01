:original_name: lts_04_0009.html

.. _lts_04_0009:

Log Search
==========

Follow the directions below to search logs by keyword and time range:

#. On the LTS console, click **Log Management**.

#. In the log group list, click the name of a log group.

#. In the log stream list, click the name of a log stream.

   Alternatively, click **Search** in the **Operation** column of the row containing the target log stream.

#. In the upper right corner, select a time range.

#. On the displayed page, enter a keyword in the search box.

#. Click |image1| to start searching.

   Logs that contain the keyword are displayed.

Search Syntax and Examples
--------------------------

**Search syntax:**

.. table:: **Table 1** Search syntax

   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | Filter                            | Description                                                                                                                                  |
   +===================================+==============================================================================================================================================+
   | Exact search by keyword           | LTS searches for logs containing the exact keyword (case-sensitive) that you specify. A keyword is the word between two adjacent delimiters. |
   |                                   |                                                                                                                                              |
   |                                   | You can add an asterisk (*) after a keyword, for example, **error\***, if you are not familiar with delimiters.                              |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | Exact search by phrase            | LTS searches for logs containing the exact phrase (case-sensitive) that you specify.                                                         |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | &&                                | Intersection of search results.                                                                                                              |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | \|\|                              | Union of search results.                                                                                                                     |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | AND                               | Intersection of search results.                                                                                                              |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | NOT                               | Logs that contain the keyword after **NOT** are excluded.                                                                                    |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | \*                                | Fuzzy search. The asterisk (*) can only be after a keyword to replace an unspecified number of characters.                                   |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | ?                                 | Fuzzy search. The question mark (?) can be put in the middle or at the end of a keyword to replace a character.                              |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+

.. note::

   Operators (such as **&&**, **\|\|**, **AND**, **NOT**, **\***, **?**, and **:**) contained in raw logs cannot be used to search for logs.

Search rules:

-  Fuzzy search is supported.

   For example, if you enter **error\***, all logs containing **error** will be displayed and those start with **error** will be highlighted.

-  Searching using multiple key-value pairs is supported. The format is *key1:value1* *key2:value2*.

   For example, if you enter **casInstanceID:in\* hostIP:x.x.x.x kkfa**, the following is displayed:

   .. code-block::

      {
          "casApplicationName": "app",
          "casEnvironmentName": "env",
          "hostName": "ecs-zc-xxxx",
          "collectTime": "15838xxxxx",
          "hostIP": "x.x.x.x",
              "logContent": "4312341341341314 kkfa dfa\\n", (Keyword)
          "appName": "testhshroma",
          "casInstanceID": "ins-111",
          "hostId": "b32dcfc0-615b-4de6-a796-dfccaxxxxxx",
          "casComponentID": "com-111"
      }

**Search examples:**

-  Search for logs containing **start**: Enter **start**.
-  Search for logs containing **start to refresh**: Enter **start to refresh**.
-  Search for logs containing both **start** and **unexpected**: Enter **start && unexpected** or **start AND unexpected**.
-  Search for logs containing **start** or **unexpected**: Enter **start \|\| unexpected**.

-  Search for the logs containing keyword **start** but not **unexpected**: Enter **start NOT unexpected**.
-  **error\***: logs that contain **error**.
-  **er?or**: logs that start with **er**, is followed by any single character, and end with **or**.
-  *query1* **AND** *query2* **NOT** *query3*: logs that contain both *query1* and *query2* but not *query3*.

.. note::

   -  Keywords are case-sensitive.
   -  The asterisk (*) and question mark (?) do not match special characters such as hyphens (-) and spaces.

.. |image1| image:: /_static/images/en-us_image_0178020286.png
