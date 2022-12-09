:original_name: lts_04_0010.html

.. _lts_04_0010:

Quick Search
============

To search for logs using a keyword repeatedly, perform the following operations to configure quick search.

Procedure
---------

#. Log in to the LTS console and choose **Log Management**.

#. In the log group list, click the name of a log group.

#. In the log stream list, click the name of a log stream.

   Alternatively, click **Search** in the **Operation** column of the row containing the target log stream.

#. On the log stream details page, click **Add Quick Search** and configure the **Name** and **Keyword** parameters.

   -  Set **Name**. A quick search name:

      -  Can contain only letters, digits, hyphens (-), underscores (_), and periods (.).
      -  Cannot start with a period (.) or underscore (_), and cannot end with a period (.).
      -  Can contain 1 to 64 characters.

   -  Set **Keyword** to a keyword that will be frequently used, for example, **error\***.

#. Click **OK**.

   Added query search filters are displayed next to **Add Quick Search**. Click the name of a quick search filter to view the search results.

Viewing Context of a Log
------------------------

You can check the log events generated before and after a log event for quick fault locating.

#. Log in to the LTS console and choose **Log Management**.

#. In the log group list, click the name of a log group.

#. In the log stream list, click the name of a log stream.

   Alternatively, click **Search** in the **Operation** column of the row containing the target log stream.

#. On the Original Logs tab page, click **View Context** in the row of a log event.

   The context of the log is displayed.
