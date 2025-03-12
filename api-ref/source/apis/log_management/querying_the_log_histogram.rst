:original_name: ListLogHistogram.html

.. _ListLogHistogram:

Querying the Log Histogram
==========================

Function
--------

This API is used to query the distribution of reported log events that contain a specified keyword over a certain period. If no keyword is specified, the distribution of all log events reported over the period is returned.

URI
---

POST /v2/{project_id}/lts/keyword-count

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                |
   +=================+=================+=================+============================================================================================================================================================+
   | project_id      | Yes             | String          | Project ID. For details about how to obtain a project ID, see :ref:`Obtaining the Project ID, Account ID, Log Group ID, and Log Stream ID <lts_api_0006>`. |
   |                 |                 |                 |                                                                                                                                                            |
   |                 |                 |                 | Minimum: **32**                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                            |
   |                 |                 |                 | Maximum: **32**                                                                                                                                            |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                   |
   +=================+=================+=================+===============================================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token obtained from IAM. For details about how to obtain a user token, see :ref:`Obtaining a User Token <lts_api_0004>`. |
   |                 |                 |                 |                                                                                                                               |
   |                 |                 |                 | Minimum: **1000**                                                                                                             |
   |                 |                 |                 |                                                                                                                               |
   |                 |                 |                 | Maximum: **2000**                                                                                                             |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type    | Yes             | String          | Set this parameter to application/json;charset=UTF-8.                                                                         |
   |                 |                 |                 |                                                                                                                               |
   |                 |                 |                 | Minimum: **30**                                                                                                               |
   |                 |                 |                 |                                                                                                                               |
   |                 |                 |                 | Maximum: **30**                                                                                                               |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                         |
   +=================+=================+=================+=====================================================================================================================+
   | start_time      | Yes             | String          | Start time, which is a timestamp accurate to millisecond.                                                           |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+
   | end_time        | Yes             | String          | End time, which is a timestamp accurate to millisecond.                                                             |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+
   | step_interval   | Yes             | Long            | Time step, in milliseconds (ms).                                                                                    |
   |                 |                 |                 |                                                                                                                     |
   |                 |                 |                 | Recommended formula:                                                                                                |
   |                 |                 |                 |                                                                                                                     |
   |                 |                 |                 | (end_time-start_time)/1000 x 1000/60, where /1000 x 1000 means rounding to an integer.                              |
   |                 |                 |                 |                                                                                                                     |
   |                 |                 |                 | .. note::                                                                                                           |
   |                 |                 |                 |                                                                                                                     |
   |                 |                 |                 |    If the calculated result is less than or equal to 1000, the value 1000 is used.                                  |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+
   | group_id        | Yes             | String          | Log group ID.                                                                                                       |
   |                 |                 |                 |                                                                                                                     |
   |                 |                 |                 | Minimum: **36**                                                                                                     |
   |                 |                 |                 |                                                                                                                     |
   |                 |                 |                 | Maximum: **36**                                                                                                     |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+
   | stream_id       | Yes             | String          | Log stream ID.                                                                                                      |
   |                 |                 |                 |                                                                                                                     |
   |                 |                 |                 | Minimum: **36**                                                                                                     |
   |                 |                 |                 |                                                                                                                     |
   |                 |                 |                 | Maximum: **36**                                                                                                     |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+
   | key_word        | Yes             | String          | A keyword is a word between two adjacent delimiters.                                                                |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+
   | is_iterative    | No              | Boolean         | Whether the log query is iterative. The default value is **false**, indicating that the log query is not iterative. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------------+-----------------------------------------------------------------------------------------------+--------------------------------+
   | Parameter       | Type                                                                                          | Description                    |
   +=================+===============================================================================================+================================+
   | count           | Long                                                                                          | Number of logs.                |
   +-----------------+-----------------------------------------------------------------------------------------------+--------------------------------+
   | histogram       | Map<String,\ :ref:`HistogramResponseBody <listloghistogram__response_histogramresponsebody>`> | Histogram result.              |
   +-----------------+-----------------------------------------------------------------------------------------------+--------------------------------+
   | isQueryComplete | Boolean                                                                                       | Whether the query is complete. |
   +-----------------+-----------------------------------------------------------------------------------------------+--------------------------------+

.. _listloghistogram__response_histogramresponsebody:

.. table:: **Table 5** HistogramResponseBody

   +-----------------+----------------------------------------------------------------+--------------------------------+
   | Parameter       | Type                                                           | Description                    |
   +=================+================================================================+================================+
   | count           | Long                                                           | Total number of log events.    |
   +-----------------+----------------------------------------------------------------+--------------------------------+
   | histogram       | :ref:`histogram <listloghistogram__response_histogram>` object | Log histogram.                 |
   +-----------------+----------------------------------------------------------------+--------------------------------+
   | isQueryComplete | Boolean                                                        | Whether the query is complete. |
   +-----------------+----------------------------------------------------------------+--------------------------------+

.. _listloghistogram__response_histogram:

.. table:: **Table 6** histogram

   ========= ====== ============================================
   Parameter Type   Description
   ========= ====== ============================================
   num       Long   Number of log events in a time range.
   startTime String Start time of a time range, in milliseconds.
   endTime   String End time of a time range, in milliseconds.
   ========= ====== ============================================

**Status code: 400**

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 8** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Querying the log histogram

.. code-block:: text

   POST https://{endpoint}/v2/{project_id}/lts/keyword-count

   {
     "group_id" : "00330565-5baf-4e0d-bd16-ba0c6b951d9a",
     "stream_id" : "715cda3b-e17f-492a-a6ca-98a1ba16ad8c",
     "end_time" : 1637820813605,
     "start_time" : 1637817213605,
     "key_word" : "test",
     "step_interval" : 6000
   }

Example Responses
-----------------

**Status code: 200**

The query is successful.

.. code-block::

   {
     "count" : 1,
     "histogram" : [ {
       "num" : 1,
       "startTime" : 1637821594579,
       "endTime" : 1637821595000
     }, {
       "num" : 0,
       "startTime" : 1637821654000,
       "endTime" : 1637821654579
     } ],
     "isQueryComplete" : true
   }

**Status code: 400**

Invalid request. Modify the request based on the description in **error_msg** before a retry.

.. code-block::

   {
     "error_code" : "LTS.0601",
     "error_msg" : "must be less than or equal to 86400000"
   }

**Status code: 500**

InternalServerError. The server has received the request but encountered an internal error.

.. code-block::

   {
     "error_code" : "LTS.0202",
     "error_msg" : "Internal Server Error"
   }

Status Codes
------------

+-------------+-----------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                   |
+=============+===============================================================================================+
| 200         | The query is successful.                                                                      |
+-------------+-----------------------------------------------------------------------------------------------+
| 400         | Invalid request. Modify the request based on the description in **error_msg** before a retry. |
+-------------+-----------------------------------------------------------------------------------------------+
| 500         | InternalServerError. The server has received the request but encountered an internal error.   |
+-------------+-----------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
