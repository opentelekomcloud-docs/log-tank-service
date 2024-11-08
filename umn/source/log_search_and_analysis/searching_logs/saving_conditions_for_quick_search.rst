:original_name: lts_05_0009.html

.. _lts_05_0009:

Saving Conditions for Quick Search
==================================

If you need to repeatedly use a keyword to search for logs, you can set and save the keyword as a quick query statement for faster log querying and analysis.


Saving Conditions for Quick Search
----------------------------------

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**. The **Log Management** page is displayed by default.

#. Click the target log group or stream. The log stream details page is displayed.

#. Click |image1| on the **Raw Logs** tab page. Enter a name and statement for quick search. By default, quick search and quick search (local cache) are enabled.


   .. figure:: /_static/images/en-us_image_0000001972864060.png
      :alt: **Figure 1** Creating quick search

      **Figure 1** Creating quick search

   -  A quick search name is used to distinguish multiple quick search statements. The name can be customized and must meet the following requirements:

      -  Can contain only letters, digits, hyphens (-), underscores (_), and periods (.).
      -  Cannot start with a period (.) or underscore (_) or end with a period (.).
      -  Can contain 1 to 64 characters.

   -  A quick search statement is used to repeatedly search for logs, for example, **error\***.

#. Click **OK**. On the **Quick Search** tab page in the left navigation pane, you can view the statements that are successfully saved.

   Click the name of a quick search statement to view log details.

Viewing Context of a Log
------------------------

You can check the logs generated before and after a log for quick fault locating.

#. On the **Raw Logs** tab page of the log details page, click |image2| to view the context.

   Details of several logs generated before and after the log are displayed.

#. On the displayed page, check the log context. For details, see :ref:`Table 1 <lts_05_0009__en-us_topic_0000001252098982_table9753194141610>`.

   .. _lts_05_0009__en-us_topic_0000001252098982_table9753194141610:

   .. table:: **Table 1** Introduction to log context viewing

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Feature                           | Description                                                                                                                                                                                                                                                                                                                                             |
      +===================================+=========================================================================================================================================================================================================================================================================================================================================================+
      | Search Rows                       | Select the number of lines of logs to be queried as required.                                                                                                                                                                                                                                                                                           |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Highlighting                      | Enter a string to be highlighted and press **Enter**.                                                                                                                                                                                                                                                                                                   |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Filter                            | Enter a string to be filtered and press **Enter**. When both **Highlighting** and **Filter** are configured, the filtered string can also be highlighted.                                                                                                                                                                                               |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Fields                            | The default field for viewing log context is **content**. Click **Fields** to view the context of other fields.                                                                                                                                                                                                                                         |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Prev                              | View half the number of **Search Rows** leading to the current position. For example, if **Search Rows** is set to 100 and you click **Prev**, 50 rows prior to the current position are displayed. In this case, the current line number is **-50**. If you click **Prev** again, the line number will become **-100**, **-150**, **-200**, and so on. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Current                           | Current log position. When **Prev** or **Update** is set, you can click **Current** to return to the position where the context starts (when the line number is 0).                                                                                                                                                                                     |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Update                            | View half the number of **Search Rows** following the current position. For example, if **Search Rows** is set to 100 and you click **Update**, 50 rows following the current position are displayed. In this case, the current line number is 50. If you click **Update** again, the line number will become **100**, **150**, **200**, and so on.     |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Summary Mode                      | -  If this mode is enabled, only the line number and content are displayed.                                                                                                                                                                                                                                                                             |
      |                                   | -  If this mode is disabled, log details are displayed.                                                                                                                                                                                                                                                                                                 |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Download                          | Only content in the **content** field can be downloaded to the local PC.                                                                                                                                                                                                                                                                                |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001612861593.png
.. |image2| image:: /_static/images/en-us_image_0000001262557500.png
