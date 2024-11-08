:original_name: lts_faq_0031.html

.. _lts_faq_0031:

What Do I Do If I Cannot View Reported Logs in LTS?
===================================================

Symptom
-------

Logs reported to LTS are not displayed on the LTS console.

Possible Causes
---------------

-  ICAgent has not been installed.
-  The collection path is incorrectly configured.
-  **ICAgent Collection** in **Configuration Center** on the LTS console is disabled.
-  The rate of writing logs into log streams or length of single-line logs exceeds what is supported.
-  The browser has slowed down because of the amount of log data.

Solution
--------

-  If ICAgent has not been installed, install it. For details, see :ref:`Installing ICAgent <lts_02_0013>`.
-  If the collection path is incorrectly configured, modify it. If the collection path is set to a directory, for example, **/var/logs/**, only **.log**, **.trace**, and **.out** files in the directory are collected. If the collection path is set to a text file name, that file is directly collected.
-  If **ICAgent Collection** is disabled, log in to the LTS console, choose **Configuration Center** > **ICAgent Collection**, and enable **ICAgent Collection**.
-  If the rate of writing logs into log streams or length of single-line logs exceeds the limit, or the browser has slowed down because of the amount of log data, use Google Chrome or Firefox to query logs.
