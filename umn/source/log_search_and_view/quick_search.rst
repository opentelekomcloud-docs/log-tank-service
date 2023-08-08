:original_name: lts_05_0009.html

.. _lts_05_0009:

Quick Search
============

To search for logs using a keyword repeatedly, perform the following operations to configure quick search.

Procedure
---------

#. On the LTS console, choose **Log Management** in the navigation pane on the left.

#. In the log group list, click |image1| on the left of a log group name.

#. In the log stream list, click the name of the target log stream.

#. On the log stream details page, click |image2| and specify **Name** and **Keyword**.

   -  A quick search name is used to distinguish multiple quick search statements. The name can be customized and must meet the following requirements:

      -  Can contain only letters, digits, hyphens (-), underscores (_), and periods (.).
      -  Cannot start with a period (.) or underscore (_) or end with a period (.).
      -  Can contain 1 to 64 characters.

   -  A quick search statement is used to repeatedly search for logs, for example, **error\***.

#. Click **OK**.

   Click the name of a quick search statement to view log details.

Viewing Context of a Log
------------------------

You can check the logs generated before and after a log for quick fault locating.

#. On the LTS console, choose **Log Management** in the navigation pane on the left.

#. In the log group list, click |image3| on the left of a log group name.

#. In the log stream list, click the name of the target log stream.

#. On the **Raw Logs** tab page, click |image4| to view the context.

   The context of the log is displayed.

#. On the displayed **View Context** page, check the log context.

   .. table:: **Table 1** Introduction to log context viewing

      +--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Feature      | Description                                                                                                                                                                                                                                                                                                                                             |
      +==============+=========================================================================================================================================================================================================================================================================================================================================================+
      | Search Rows  | Number of rows to search. The options are 100, 200, and 500.                                                                                                                                                                                                                                                                                            |
      +--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Highlighting | Enter a string to be highlighted and press **Enter**.                                                                                                                                                                                                                                                                                                   |
      +--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Filter       | Enter a string to be filtered and press **Enter**. When both **Highlighting** and **Filter** are configured, the filtered string can also be highlighted.                                                                                                                                                                                               |
      +--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Fields       | The default field for viewing log context is **content**. Click **Fields** to view the context of other fields.                                                                                                                                                                                                                                         |
      +--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Prev         | View half the number of **Search Rows** leading to the current position. For example, if **Search Rows** is set to 100 and you click **Prev**, 50 rows prior to the current position are displayed. In this case, the current line number is **-50**. If you click **Prev** again, the line number will become **-100**, **-150**, **-200**, and so on. |
      +--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Current      | Current log position. When **Prev** or **Update** is set, you can click **Current** to return to the position where the context starts (when the line number is 0).                                                                                                                                                                                     |
      +--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Update       | View half the number of **Search Rows** following the current position. For example, if **Search Rows** is set to 100 and you click **Update**, 50 rows following the current position are displayed. In this case, the current line number is 50. If you click **Update** again, the line number will become **100**, **150**, **200**, and so on.     |
      +--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001463903813.png
.. |image2| image:: /_static/images/en-us_image_0000001612861593.png
.. |image3| image:: /_static/images/en-us_image_0000001262717056.png
.. |image4| image:: /_static/images/en-us_image_0000001262557500.png
