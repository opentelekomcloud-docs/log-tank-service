:original_name: DeleteLogStream.html

.. _DeleteLogStream:

Deleting a Log Stream
=====================

Function
--------

This API is used to delete a specified log stream from a specified log group. If log transfer is enabled for a log stream, you need to disable the log transfer before the deletion.

URI
---

DELETE /v2/{project_id}/groups/{log_group_id}/streams/{log_stream_id}

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                      |
   +=================+=================+=================+==================================================================================================================================================================+
   | project_id      | Yes             | String          | Project ID. For details about how to obtain a project ID, see :ref:`Obtaining the Project ID, Account ID, Log Group ID, and Log Stream ID <lts_api_0006>`.       |
   |                 |                 |                 |                                                                                                                                                                  |
   |                 |                 |                 | Minimum: **32**                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                  |
   |                 |                 |                 | Maximum: **32**                                                                                                                                                  |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_group_id    | Yes             | String          | Log group ID. For details about how to obtain a log group ID, see :ref:`Obtaining the Project ID, Account ID, Log Group ID, and Log Stream ID <lts_api_0006>`.   |
   |                 |                 |                 |                                                                                                                                                                  |
   |                 |                 |                 | Minimum: **36**                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                  |
   |                 |                 |                 | Maximum: **36**                                                                                                                                                  |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_stream_id   | Yes             | String          | Log stream ID. For details about how to obtain a log stream ID, see :ref:`Obtaining the Project ID, Account ID, Log Group ID, and Log Stream ID <lts_api_0006>`. |
   |                 |                 |                 |                                                                                                                                                                  |
   |                 |                 |                 | Minimum: **36**                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                  |
   |                 |                 |                 | Maximum: **36**                                                                                                                                                  |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

**Status code: 400**

.. table:: **Table 3** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 401**

.. table:: **Table 4** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Deleting a log stream

.. code-block:: text

   DELETE https://{endpoint}/v2/{project_id}/groups/{log_group_id}/streams/{log_stream_id}

   /v2/{project_id}/groups/{log_group_id}/streams/{log_stream_id}

Example Responses
-----------------

**Status code: 400**

BadRequest. The request is invalid. Modify the request based on the description in **error_msg** before a retry.

.. code-block::

   {
     "error_code" : "LTS.0208",
     "error_msg" : "The log stream does not existed"
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
     "error_code" : "LTS.0203",
     "error_msg" : "Failed to delete Log stream"
   }

Status Codes
------------

+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Status Code                       | Description                                                                                                                                                                                  |
+===================================+==============================================================================================================================================================================================+
| 204                               | The request is successful and the log stream has been deleted.                                                                                                                               |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 400                               | BadRequest. The request is invalid. Modify the request based on the description in **error_msg** before a retry.                                                                             |
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
