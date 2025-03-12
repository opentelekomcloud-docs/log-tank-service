:original_name: UpdateLogStream.html

.. _UpdateLogStream:

Modifying a Log Stream
======================

Function
--------

This API is used to modify the log retention duration of a specified log stream.

URI
---

PUT /v2/{project_id}/groups/{log_group_id}/streams-ttl/{log_stream_id}

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                      |
   +=================+=================+=================+==================================================================================================================================================================+
   | project_id      | Yes             | String          | Project ID. For details about how to obtain a project ID, see :ref:`Obtaining the Project ID, Account ID, Log Group ID, and Log Stream ID <lts_api_0006>`.       |
   |                 |                 |                 |                                                                                                                                                                  |
   |                 |                 |                 | Minimum length: 36 characters.                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                  |
   |                 |                 |                 | Maximum length: 36 characters.                                                                                                                                   |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_group_id    | Yes             | String          | Log group ID. For details about how to obtain a log group ID, see :ref:`Obtaining the Project ID, Account ID, Log Group ID, and Log Stream ID <lts_api_0006>`.   |
   |                 |                 |                 |                                                                                                                                                                  |
   |                 |                 |                 | Minimum length: 36 characters.                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                  |
   |                 |                 |                 | Maximum length: 36 characters.                                                                                                                                   |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_stream_id   | Yes             | String          | Log stream ID. For details about how to obtain a log stream ID, see :ref:`Obtaining the Project ID, Account ID, Log Group ID, and Log Stream ID <lts_api_0006>`. |
   |                 |                 |                 |                                                                                                                                                                  |
   |                 |                 |                 | Minimum length: 36 characters.                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                  |
   |                 |                 |                 | Maximum length: 36 characters.                                                                                                                                   |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                     |
   +=================+=================+=================+=================================================================================================================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token obtained from IAM. For details about how to obtain a user token, see :ref:`Obtaining a User Token <lts_api_0004>`. Minimum length: 1000 characters; Maximum length: 2000 characters. |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type    | Yes             | String          | Set this parameter to **application/json;charset=UTF-8**.                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                                 |
   |                 |                 |                 | Minimum length: 30 characters.                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                 |
   |                 |                 |                 | Maximum length: 30 characters.                                                                                                                                                                  |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+----------------------------------------------------------------------+--------------------------------+
   | Parameter       | Mandatory       | Type                                                                 | Description                    |
   +=================+=================+======================================================================+================================+
   | ttl_in_days     | Yes             | Integer                                                              | Log retention duration (days). |
   |                 |                 |                                                                      |                                |
   |                 |                 |                                                                      | Minimum: **1**                 |
   |                 |                 |                                                                      |                                |
   |                 |                 |                                                                      | Maximum: **365**               |
   +-----------------+-----------------+----------------------------------------------------------------------+--------------------------------+
   | tags            | No              | Array of :ref:`tagsBody <updatelogstream__request_tagsbody>` objects | Tag field information.         |
   +-----------------+-----------------+----------------------------------------------------------------------+--------------------------------+

.. _updatelogstream__request_tagsbody:

.. table:: **Table 4** tagsBody

   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                                                |
   +===========+===========+========+============================================================================================================================================================+
   | key       | Yes       | String | Tag key. Use only UTF-8 letters, digits, spaces, and the following characters: .:=+-@. Do not start with an underscore (). Max 128 characters are allowed. |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value     | Yes       | String | Tag value. Use only UTF-8 letters, digits, spaces, and the following characters: ``_.:/=+-@.`` Max 255 characters are allowed.                             |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   ============== ======= ==================================
   Parameter      Type    Description
   ============== ======= ==================================
   creation_time  Long    Time when a log stream is created.
   log_topic_name String  Name of a log stream.
   log_topic_id   String  Log stream ID.
   ttl_in_days    Integer Log retention duration (days).
   ============== ======= ==================================

**Status code: 400**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 401**

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 8** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 9** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Modify a log stream.

.. code-block:: text

   PUT https://{endpoint}/v2/{project_id}/groups/{log_group_id}/streams-ttl/{log_stream_id}

   {
     "ttl_in_days" : 8
   }

Example Responses
-----------------

**Status code: 200**

The request has succeeded and the log group has been modified.

.. code-block::

   {
     "creation_time" : 1629947408497,
     "log_topic_name" : "string",
     "log_topic_id" : "string",
     "ttl_in_days" : 8
   }

**Status code: 400**

BadRequest. Invalid request. Modify the request based on the description in **error_msg** before a retry.

.. code-block::

   {
     "error_code" : "LTS.0009",
     "error_msg" : "Failed to validate the request body"
   }

**Status code: 401**

AuthFailed. Authentication failed. Check the token and try again.

.. code-block::

   {
     "error_code" : "LTS.0414",
     "error_msg" : "Invalid token"
   }

**Status code: 403**

Forbidden. The request is rejected. The server has received the request and understood it, but refuses to respond to it. The client should not repeat the request without modifications.

.. code-block::

   {
     "error_code" : "LTS.0001",
     "error_msg" : "Invalid projectId"
   }

**Status code: 500**

InternalServerError. The server has received the request but encountered an internal error.

.. code-block::

   {
     "error_code" : "LTS.0204",
     "error_msg" : "Failed to update log stream"
   }

Status Codes
------------

+-------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                                                                                                              |
+=============+==========================================================================================================================================================================================+
| 200         | The request has succeeded and the log group has been modified.                                                                                                                           |
+-------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 400         | BadRequest. Invalid request. Modify the request based on the description in **error_msg** before a retry.                                                                                |
+-------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 401         | AuthFailed. Authentication failed. Check the token and try again.                                                                                                                        |
+-------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 403         | Forbidden. The request is rejected. The server has received the request and understood it, but refuses to respond to it. The client should not repeat the request without modifications. |
+-------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 500         | InternalServerError. The server has received the request but encountered an internal error.                                                                                              |
+-------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 503         | ServiceUnavailable. The requested service is unavailable.                                                                                                                                |
+-------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
