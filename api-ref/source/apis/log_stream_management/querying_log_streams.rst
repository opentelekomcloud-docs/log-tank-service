:original_name: ListLogStreams.html

.. _ListLogStreams:

Querying Log Streams
====================

Function
--------

This API is used to query log streams.

URI
---

GET /v2/{project_id}/log-streams

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

   +-----------------+-----------------+-----------------+------------------+
   | Parameter       | Mandatory       | Type            | Description      |
   +=================+=================+=================+==================+
   | log_group_name  | No              | String          | Log group name.  |
   |                 |                 |                 |                  |
   |                 |                 |                 | Minimum: **1**   |
   |                 |                 |                 |                  |
   |                 |                 |                 | Maximum: **64**  |
   +-----------------+-----------------+-----------------+------------------+
   | log_stream_name | No              | String          | Log stream name. |
   |                 |                 |                 |                  |
   |                 |                 |                 | Minimum: **1**   |
   |                 |                 |                 |                  |
   |                 |                 |                 | Maximum: **64**  |
   +-----------------+-----------------+-----------------+------------------+

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
   | Content-Type    | Yes             | String          | Set this parameter to application/json;charset=UTF-8.                                                                         |
   |                 |                 |                 |                                                                                                                               |
   |                 |                 |                 | Minimum: **30**                                                                                                               |
   |                 |                 |                 |                                                                                                                               |
   |                 |                 |                 | Maximum: **30**                                                                                                               |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-------------+------------------------------------------------------------------------------------------------+---------------------+
   | Parameter   | Type                                                                                           | Description         |
   +=============+================================================================================================+=====================+
   | log_streams | Array of :ref:`LogStreamNoIsFavorite <listlogstreams__response_logstreamnoisfavorite>` objects | List of log groups. |
   +-------------+------------------------------------------------------------------------------------------------+---------------------+

.. _listlogstreams__response_logstreamnoisfavorite:

.. table:: **Table 5** LogStreamNoIsFavorite

   =============== ================== ==================================
   Parameter       Type               Description
   =============== ================== ==================================
   creation_time   Long               Time when a log stream is created.
   log_stream_id   String             Log stream ID.
   log_stream_name String             Log stream name.
   tag             Map<String,String> Log stream tag.
   filter_count    Integer            Number of filters.
   =============== ================== ==================================

**Status code: 400**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

If you leave the request body empty, all log streams are queried. If **log_group_name** and **log_stream_name** are specified, the corresponding log stream is queried.

.. code-block:: text

   GET https://{endpoint}/v2/{project_id}/log-streams

   /v2/{project_id}/log-streams /v2/{project_id}/log-streams?log_group_name=lts-group-txxxx
   /v2/{project_id}/log-streams?log_stream_name=lts-xunjian-topic-xxxx
   /v2/{project_id}/log-streams?log_stream_name=lts-xunjian-topic-xxxx&log_group_name=lts-group-xxx

Example Responses
-----------------

**Status code: 200**

Log stream information is returned.

.. code-block::

   {
     "log_streams" : [ {
       "creation_time" : 1633600371062,
       "log_stream_name" : "lts-topic-test2",
       "tag" : {
         "_sys_enterprise_project_id" : "0",
         "W" : "J"
       },
       "filter_count" : 0,
       "log_stream_id" : "c4de0538-53e6-41fd-b951-a8669fce58d7"
     } ]
   }

**Status code: 400**

Invalid request. Modify the request based on the description in **error_msg** before a retry.

.. code-block::

   {
     "error_code" : "LTS.0205",
     "error_msg" : "The log stream name has been existed"
   }

**Status code: 500**

The server has received the request but encountered an internal error.

.. code-block::

   {
     "error_code" : "LTS.0010",
     "error_msg" : "The system encountered an internal error"
   }

Status Codes
------------

+-------------+-----------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                   |
+=============+===============================================================================================+
| 200         | Log stream information is returned.                                                           |
+-------------+-----------------------------------------------------------------------------------------------+
| 400         | Invalid request. Modify the request based on the description in **error_msg** before a retry. |
+-------------+-----------------------------------------------------------------------------------------------+
| 500         | The server has received the request but encountered an internal error.                        |
+-------------+-----------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
