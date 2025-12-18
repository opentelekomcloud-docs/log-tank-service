:original_name: lts_05_0007.html

.. _lts_05_0007:

Creating a Quick Analysis Task
==============================

Logs contain information such as system performance and business status. For example, the frequency of keyword **ERROR** indicates the system health, and the frequency of keyword **BUY** indicates the business activity. You can use the quick analysis function to query specified log keywords. LTS collects statistics on the keywords and generates metric data, so that you can learn about the system performance and business in real time.

-  The quick analysis function rapidly samples field value distributions without analyzing all data. The default number of samples is 100,000, with a maximum of 10 million. The more samples taken, the slower the analysis process. You can specify the number of samples for quick analysis on the **Index Settings** tab page. For details, see :ref:`Configuring Log Indexing <lts_05_0008>`.

-  Logs can be filtered by query time and criteria for analysis.

   Quick analysis is to analyze the logs queried by query statements. When the number of queried logs is 0, no result is displayed for quick analysis.

-  Quick analysis can be used to generate query statements.

   You can click an analysis result to automatically generate a query statement, query logs, and generate a new quick analysis.

-  If quick analysis is not enabled within the analysis time range, a field does not exist, or a field value is null, the analysis result of the field is **null**.

   -  When you click **null** to add a string field to the search box, *Field* **: "null"OR NOT** *Field* **: \*** will be displayed.
   -  When you click **null** to add a float or long field to the search box, **NOT** *Field* **: \*** will be displayed.
   -  If quick analysis is not enabled, the column-store data used for analysis is not stored, and the analysis result is **null**. In this case, log search is meaningless and no log may be matched.

Prerequisites
-------------

Quick analysis is conducted on fields extracted from structured logs. :ref:`Structure <lts_0821>` raw logs before you create a quick analysis task.


Creating a Quick Analysis Task
------------------------------

Quick analysis is performed on a per-log-stream basis. You can create a quick analysis task as follows:

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**. The **Log Management** page is displayed by default.
#. Click the target log group or stream to access the log details page.
#. On the **Log Search** tab page, click |image1| next to **Quick Analysis** to go to the **Index Settings** tab page. Under **Index Fields**, click **Auto Configure** to generate index fields automatically. Enable quick analysis for these fields.
#. Click **OK**. The quick analysis task is created.

   -  **abc** displayed in front of a field indicates that the field is of the string type.
   -  **1.2** displayed in front of a field indicates that the field is of the float type.
   -  **123** displayed in front of a field indicates that the field is of the long type.
   -  The maximum length of a field for quick analysis is 2,000 bytes.
   -  The quick analysis field area displays the first 100 records.

#. Set whether to hide or display fields.

   -  To hide a field, click |image2| next to the field.
   -  To hide all fields, click |image3| next to **Fields**.
   -  To display a hidden field, click |image4| next to the field.
   -  To display all fields, click |image5| next to **Hidden Fields**.

.. |image1| image:: /_static/images/en-us_image_0000001579917292.png
.. |image2| image:: /_static/images/en-us_image_0000002348409952.png
.. |image3| image:: /_static/images/en-us_image_0000002228297244.png
.. |image4| image:: /_static/images/en-us_image_0000002348569852.png
.. |image5| image:: /_static/images/en-us_image_0000002228299512.png
