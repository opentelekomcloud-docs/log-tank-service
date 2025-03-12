:original_name: ListTimeLineTrafficStatistics.html

.. _ListTimeLineTrafficStatistics:

Querying Resources by Time Segment
==================================

Function
--------

This API is used to query resources by time segment.

URI
---

POST /v2/{project_id}/lts/timeline-traffic-statistics

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

.. table:: **Table 2** Query Parameters

   +-----------+-----------+--------+-----------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                       |
   +===========+===========+========+===================================================================================+
   | timezone  | Yes       | String | Time zone, for example, **Asia/Shanghai**, **Europe/Paris**, or **Africa/Cairo**. |
   +-----------+-----------+--------+-----------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                   |
   +=================+=================+=================+===============================================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token obtained from IAM. For details about how to obtain a user token, see :ref:`Obtaining a User Token <lts_api_0004>`. |
   |                 |                 |                 |                                                                                                                               |
   |                 |                 |                 | Minimum: **1000**                                                                                                             |
   |                 |                 |                 |                                                                                                                               |
   |                 |                 |                 | Maximum: **2000**                                                                                                             |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type    | Yes             | String          | Set this parameter to **application/json;charset=UTF-8**.                                                                     |
   |                 |                 |                 |                                                                                                                               |
   |                 |                 |                 | Minimum: **30**                                                                                                               |
   |                 |                 |                 |                                                                                                                               |
   |                 |                 |                 | Maximum: **30**                                                                                                               |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 4** Request body parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                               |
   +=================+=================+=================+===========================================================================================+
   | start_time      | Yes             | Long            | Start timestamp of the query, in milliseconds. A maximum of 30 days are supported.        |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+
   | end_time        | Yes             | Long            | End timestamp, in milliseconds.                                                           |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+
   | period          | Yes             | Integer         | Query interval, in hours. The value ranges from 1 to 24.                                  |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+
   | resource_type   | Yes             | String          | Resource type: The value is log_group / log_stream / tenant.                              |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+
   | search_type     | Yes             | String          | Type of traffic to be queried: **write**, **index**, or **storage**.                      |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+
   | resource_id     | No              | String          | Resource ID.                                                                              |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | When resource type is set to **log_group**, **resource_id** indicates the log group ID.   |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | When resource type is set to **log_stream**, **resource_id** indicates the log stream ID. |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   +-----------+-------------------------------------------------------------------------------------+------------------+
   | Parameter | Type                                                                                | Description      |
   +===========+=====================================================================================+==================+
   | results   | Array of :ref:`Resulits <listtimelinetrafficstatistics__response_resulits>` objects | Response result. |
   +-----------+-------------------------------------------------------------------------------------+------------------+

.. _listtimelinetrafficstatistics__response_resulits:

.. table:: **Table 6** Resulits

   ========= ====== ===========================
   Parameter Type   Description
   ========= ====== ===========================
   timestamp Long   Timestamp, in milliseconds.
   value     Double Traffic, in bytes.
   ========= ====== ===========================

**Status code: 400**

.. table:: **Table 7** Response body parameters

   ============ ====== ==============
   Parameter    Type   Description
   ============ ====== ==============
   errorCode    String Error code.
   errorMessage String Error message.
   ============ ====== ==============

**Status code: 500**

.. table:: **Table 8** Response body parameters

   ============ ====== ==============
   Parameter    Type   Description
   ============ ====== ==============
   errorCode    String Error code.
   errorMessage String Error message.
   ============ ====== ==============

Example Requests
----------------

Querying Resources by Time Segment

.. code-block:: text

   POST v2/2a473356cca5487f8373be891bffc1cf/lts/timeline-traffic-statistics?timezone=XX/XX

   {
     "start_time" : 1668614400000,
     "end_time" : 1668787200000,
     "search_type" : "write",
     "period" : 1,
     "resource_type" : "tenant"
   }

Example Responses
-----------------

**Status code: 200**

Query succeeded.

.. code-block::

   {
     "results" : [ {
       "timestamp" : 1669046400000,
       "value" : 8.24859442E7
     }, {
       "timestamp" : 1669071600000,
       "value" : 0
     }, {
       "timestamp" : 1669161600000,
       "value" : 9.06895742E7
     }, {
       "timestamp" : 1669215600000,
       "value" : 8.81524816E7
     } ]
   }

**Status code: 400**

Invalid request. Modify the request based on the description in **error_msg** before a retry.

.. code-block::

   {
     "errorCode" : "LTS.0009",
     "errorMessage" : "resource_id must not be empty"
   }

**Status code: 500**

The server has received the request but encountered an internal error.

.. code-block::

   {
     "errorCode" : "LTS.0203",
     "errorMessage" : "Internal Server Error"
   }

Status Codes
------------

+-------------+-----------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                   |
+=============+===============================================================================================+
| 200         | Query succeeded.                                                                              |
+-------------+-----------------------------------------------------------------------------------------------+
| 400         | Invalid request. Modify the request based on the description in **error_msg** before a retry. |
+-------------+-----------------------------------------------------------------------------------------------+
| 500         | The server has received the request but encountered an internal error.                        |
+-------------+-----------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
