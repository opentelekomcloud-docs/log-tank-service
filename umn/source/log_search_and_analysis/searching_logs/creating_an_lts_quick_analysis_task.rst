:original_name: lts_05_0007.html

.. _lts_05_0007:

Creating an LTS Quick Analysis Task
===================================

Logs contain information such as system performance and business status. For example, the frequency of keyword **ERROR** indicates the system health, and the frequency of keyword **BUY** indicates the business activity. You can use the quick analysis function to query specified log keywords. LTS collects statistics on the keywords and generates metric data, so that you can learn about the system performance and business in real time.

.. note::

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

#. Click the target log group or stream. The log stream details page is displayed.

#. You can create a quick analysis task in either of the following ways:

   a. Click |image1| to go to the setting details page. Under **Index Fields**, enable **Quick Analysis** when adding a field.
   b. On the **Cloud Structuring Parsing** tab page, enable **Auto Configuration and Analysis**. It is enabled by default. This enables structured fields for configuring indexes and quick analysis.

#. On the **Raw Logs** tab page, click **Set Quick Analysis**. On the displayed **Index Settings** tab page, add fields for quick analysis.


   .. figure:: /_static/images/en-us_image_0000001795947797.png
      :alt: **Figure 1** Creating a quick analysis task

      **Figure 1** Creating a quick analysis task

#. Click **OK**. The quick analysis task is created.

   .. note::

      -  |image2| indicates a field of the **string** type.
      -  |image3| indicates a field of the **float** type.
      -  |image4| indicates a field of the **long** type.
      -  The maximum length of a field for quick analysis is 2000 bytes.
      -  The quick analysis field area displays the first 100 records.

.. |image1| image:: /_static/images/en-us_image_0000001579917292.png
.. |image2| image:: /_static/images/en-us_image_0000001588482889.png
.. |image3| image:: /_static/images/en-us_image_0000001298698089.png
.. |image4| image:: /_static/images/en-us_image_0000001252258790.png
