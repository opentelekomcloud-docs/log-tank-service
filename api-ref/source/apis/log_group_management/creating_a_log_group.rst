:original_name: CreateLogGroup.html

.. _CreateLogGroup:

Creating a Log Group
====================

Function
--------

This API is used to create a log group.

URI
---

POST /v2/{project_id}/groups

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

   +----------------------+-----------------+---------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter            | Mandatory       | Type                                                                | Description                                                                                                                                      |
   +======================+=================+=====================================================================+==================================================================================================================================================+
   | log_group_name       | Yes             | String                                                              | Name of the log group to be created.                                                                                                             |
   |                      |                 |                                                                     |                                                                                                                                                  |
   |                      |                 |                                                                     | The configuration rules are as follows:                                                                                                          |
   |                      |                 |                                                                     |                                                                                                                                                  |
   |                      |                 |                                                                     | A name can contain 1 to 64 characters,                                                                                                           |
   |                      |                 |                                                                     |                                                                                                                                                  |
   |                      |                 |                                                                     | including only letters, digits, underscores (_), hyphens (-), and periods (.). It cannot start with a period or underscore or end with a period. |
   |                      |                 |                                                                     |                                                                                                                                                  |
   |                      |                 |                                                                     | Minimum: **1**                                                                                                                                   |
   |                      |                 |                                                                     |                                                                                                                                                  |
   |                      |                 |                                                                     | Maximum: **64**                                                                                                                                  |
   +----------------------+-----------------+---------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | ttl_in_days          | Yes             | Integer                                                             | Log retention duration. (Default: 30 days)                                                                                                       |
   |                      |                 |                                                                     |                                                                                                                                                  |
   |                      |                 |                                                                     | Minimum: **1**                                                                                                                                   |
   |                      |                 |                                                                     |                                                                                                                                                  |
   |                      |                 |                                                                     | Maximum: **365**                                                                                                                                 |
   +----------------------+-----------------+---------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                 | No              | Array of :ref:`tagsBody <createloggroup__request_tagsbody>` objects | Tag field information.                                                                                                                           |
   +----------------------+-----------------+---------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_group_name_alias | No              | String                                                              | Log group alias.                                                                                                                                 |
   +----------------------+-----------------+---------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+

.. _createloggroup__request_tagsbody:

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

**Status code: 201**

.. table:: **Table 5** Response body parameters

   +-----------------------+-----------------------+------------------------------+
   | Parameter             | Type                  | Description                  |
   +=======================+=======================+==============================+
   | log_group_id          | String                | ID of the created log group. |
   |                       |                       |                              |
   |                       |                       | Minimum: **36**              |
   |                       |                       |                              |
   |                       |                       | Maximum: **36**              |
   +-----------------------+-----------------------+------------------------------+

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

**Status code: 503**

.. table:: **Table 10** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Creating a log group

.. code-block:: text

   POST https://{endpoint}/v2/{project_id}/groups

   {
     "log_group_name" : "lts-group-01nh",
     "ttl_in_days" : 7
   }

Example Responses
-----------------

**Status code: 201**

The request is successful and the log group has been created.

.. code-block::

   {
     "log_group_id" : "b6b9332b-091f-4b22-b810-264318d2d664"
   }

**Status code: 400**

BadRequest. The request is invalid. Modify the request based on the description in **error_msg** before a retry.

.. code-block::

   {
     "error_code" : "LTS.0009",
     "error_msg" : "Failed to validate the request body"
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
     "error_code" : "LTS.0102",
     "error_msg" : "Failed to create log group"
   }

Status Codes
------------

+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Status Code                       | Description                                                                                                                                                                                  |
+===================================+==============================================================================================================================================================================================+
| 201                               | The request is successful and the log group has been created.                                                                                                                                |
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
| 503                               | ServiceUnavailable.                                                                                                                                                                          |
|                                   |                                                                                                                                                                                              |
|                                   | The requested service is unavailable.                                                                                                                                                        |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
