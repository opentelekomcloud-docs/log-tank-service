:original_name: ListLogStream.html

.. _ListLogStream:

Querying All Log Streams in a Specified Log Group
=================================================

Function
--------

This API is used to query information about all log streams in a specified log group.

URI
---

GET /v2/{project_id}/groups/{log_group_id}/streams

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                    |
   +=================+=================+=================+================================================================================================================================================================+
   | project_id      | Yes             | String          | Project ID. For details about how to obtain a project ID, see :ref:`Obtaining the Project ID, Account ID, Log Group ID, and Log Stream ID <lts_api_0006>`.     |
   |                 |                 |                 |                                                                                                                                                                |
   |                 |                 |                 | Minimum: **32**                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                |
   |                 |                 |                 | Maximum: **32**                                                                                                                                                |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_group_id    | Yes             | String          | Log group ID. For details about how to obtain a log group ID, see :ref:`Obtaining the Project ID, Account ID, Log Group ID, and Log Stream ID <lts_api_0006>`. |
   |                 |                 |                 |                                                                                                                                                                |
   |                 |                 |                 | Minimum: **36**                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                |
   |                 |                 |                 | Maximum: **36**                                                                                                                                                |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-------------+-------------------------------------------------------------------------------------+-------------+
   | Parameter   | Type                                                                                | Description |
   +=============+=====================================================================================+=============+
   | log_streams | Array of :ref:`LogStreamResBody <listlogstream__response_logstreamresbody>` objects | Log stream. |
   +-------------+-------------------------------------------------------------------------------------+-------------+

.. _listlogstream__response_logstreamresbody:

.. table:: **Table 4** LogStreamResBody

   +-----------------+--------------------+-------------------------------------------+
   | Parameter       | Type               | Description                               |
   +=================+====================+===========================================+
   | creation_time   | Long               | Creation time.                            |
   +-----------------+--------------------+-------------------------------------------+
   | log_stream_id   | String             | Log stream ID.                            |
   +-----------------+--------------------+-------------------------------------------+
   | log_stream_name | String             | Log stream name.                          |
   +-----------------+--------------------+-------------------------------------------+
   | tag             | Map<String,String> | Log stream tags.                          |
   +-----------------+--------------------+-------------------------------------------+
   | filter_count    | Integer            | Number of filters.                        |
   +-----------------+--------------------+-------------------------------------------+
   | is_favorite     | Boolean            | Whether to add a log stream to favorites. |
   +-----------------+--------------------+-------------------------------------------+

**Status code: 401**

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

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

Querying All Log Streams in a Specified Log Group

.. code-block:: text

   GET https://{endpoint}/v2/{project_id}/groups/{log_group_id}/streams

   /v2/{project_id}/groups/{log_group_id}/streams

Example Responses
-----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
     "log_streams" : [ {
       "creation_time" : 1630549842955,
       "log_stream_name" : "lts-stream-02kh",
       "log_stream_id" : "c54dbc58-0fd8-48ed-b007-6d54981427a7",
       "filter_count" : 0
     } ]
   }

**Status code: 401**

AuthFailed. Authentication failed. Check the token and try again.

.. code-block::

   {
     "error_code" : "LTS.0003",
     "error_msg" : "Invalid token"
   }

**Status code: 403**

Forbidden.The request has been rejected.The server has received the request and understood it, but refuses to respond to it. The client should not repeat the request without modifications.

.. code-block::

   {
     "error_code" : "LTS.0001",
     "error_msg" : "Invalid projectId"
   }

**Status code: 500**

InternalServerError.

The server has received the request but encountered an internal error.

.. code-block::

   {
     "error_code" : "LTS.0010",
     "error_msg" : "The system encountered an internal error"
   }

Status Codes
------------

+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Status Code                       | Description                                                                                                                                                                                  |
+===================================+==============================================================================================================================================================================================+
| 200                               | The request is successful.                                                                                                                                                                   |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 401                               | AuthFailed. Authentication failed. Check the token and try again.                                                                                                                            |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 403                               | Forbidden.The request has been rejected.The server has received the request and understood it, but refuses to respond to it. The client should not repeat the request without modifications. |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 500                               | InternalServerError.                                                                                                                                                                         |
|                                   |                                                                                                                                                                                              |
|                                   | The server has received the request but encountered an internal error.                                                                                                                       |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
