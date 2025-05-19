:original_name: lts_05_0007.html

.. _lts_05_0007:

Creating an LTS Quick Analysis Task
===================================

Logs contain information such as system performance and business status. For example, the frequency of keyword **ERROR** indicates the system health, and the frequency of keyword **BUY** indicates the business activity. You can use the quick analysis function to query specified log keywords. LTS collects statistics on the keywords and generates metric data, so that you can learn about the system performance and business in real time.

-  Supports analysis on first 100,000 logs.

   The purpose of quick analysis is to quickly return the distribution and change trend of field values. It does not analyze all data, but only samples.

-  Logs can be filtered by query time and criteria for analysis.

   Quick analysis is to analyze the logs queried by query statements. When the number of queried logs is 0, no result is displayed for quick analysis.

-  Quick analysis can be used to generate query statements.

   You can click an analysis result to automatically generate a query statement, query logs, and generate a new quick analysis.

-  The maximum length of a field for quick analysis is 2 KB.
-  The distribution statistics in quick analysis field area displays the first 100 records.
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
#. Click the target log group or stream to access the log stream details page.
#. On the **Log Search** tab page, click |image1| next to **Quick Analysis** to go to the **Index Settings** tab page. Under **Index Fields**, enable quick analysis when adding a field.
#. Click **OK**. The quick analysis task is created.

   -  |image2| indicates a field of the **string** type.
   -  |image3| indicates a field of the **float** type.
   -  |image4| indicates a field of the **long** type.
   -  The maximum length of a field for quick analysis is 2,000 bytes.
   -  The quick analysis field area displays the first 100 records.

.. |image1| image:: /_static/images/en-us_image_0000001579917292.png
.. |image2| image:: /_static/images/en-us_image_0000002159604008.png
.. |image3| image:: /_static/images/en-us_image_0000002195084841.png
.. |image4| image:: /_static/images/en-us_image_0000002159763768.png
