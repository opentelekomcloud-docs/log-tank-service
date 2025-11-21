:original_name: lts_05_0009.html

.. _lts_05_0009:

Saving Search and Analysis Statements
=====================================

To repeatedly use a search and analysis statement, you can set and save it as a quick search statement for faster log searching and analysis.

Creating a Quick Search
-----------------------

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**. The **Log Management** page is displayed by default.
#. Click the target log group or stream to access the log details page.
#. Click |image1| on the **Log Search** tab page. Enter a name and statement for quick search. By default, quick search and quick search (local cache) are enabled.

   -  A quick search name is used to distinguish multiple quick search statements. The name can be customized and must meet the following requirements:

      -  Can contain only letters, digits, hyphens (-), underscores (_), and periods (.).
      -  Cannot start with a period (.) or underscore (_) or end with a period (.).
      -  Can contain 1 to 64 characters.

   -  A quick search statement is used to repeatedly search for logs, for example, **error\***.

#. Click **OK**. On the **Quick Search** tab page in the left navigation pane, you can view the statements that are successfully saved.

   -  To view the log search result of a quick search statement, click its name.
   -  To modify a quick search statement, move the cursor to the statement and click |image2| next to it. On the **Edit Quick Search** dialog box displayed, modify the statement and click **OK**.
   -  To delete a quick search statement, move the cursor to the statement and click |image3| next to it. On the **Delete Quick Search** dialog box displayed, click **OK**. Quick search cannot be performed with a deleted statement. Exercise caution when performing this operation.

.. |image1| image:: /_static/images/en-us_image_0000001612861593.png
.. |image2| image:: /_static/images/en-us_image_0000002282520389.png
.. |image3| image:: /_static/images/en-us_image_0000002282400489.png
