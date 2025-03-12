:original_name: ListLogGroups.html

.. _ListLogGroups:

Querying All Log Groups of an Account
=====================================

Function
--------

This API is used to query all log groups of an account.

URI
---

GET /v2/{project_id}/groups

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

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +------------+---------------------------------------------------------------------+------------------------+
   | Parameter  | Type                                                                | Description            |
   +============+=====================================================================+========================+
   | log_groups | Array of :ref:`LogGroup <listloggroups__response_loggroup>` objects | Log group information. |
   +------------+---------------------------------------------------------------------+------------------------+

.. _listloggroups__response_loggroup:

.. table:: **Table 4** LogGroup

   +-----------------------+-----------------------+--------------------------------+
   | Parameter             | Type                  | Description                    |
   +=======================+=======================+================================+
   | creation_time         | Long                  | Log group creation time.       |
   +-----------------------+-----------------------+--------------------------------+
   | log_group_name        | String                | Log group name.                |
   |                       |                       |                                |
   |                       |                       | Minimum: **1**                 |
   |                       |                       |                                |
   |                       |                       | Maximum: **64**                |
   +-----------------------+-----------------------+--------------------------------+
   | log_group_id          | String                | Log group ID.                  |
   |                       |                       |                                |
   |                       |                       | Minimum: **36**                |
   |                       |                       |                                |
   |                       |                       | Maximum: **36**                |
   +-----------------------+-----------------------+--------------------------------+
   | ttl_in_days           | Integer               | Log retention duration (days). |
   |                       |                       |                                |
   |                       |                       | Minimum: **1**                 |
   |                       |                       |                                |
   |                       |                       | Maximum: **365**               |
   +-----------------------+-----------------------+--------------------------------+
   | tag                   | Map<String,String>    | Log group tag.                 |
   +-----------------------+-----------------------+--------------------------------+

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

Querying All Log Groups of an Account

.. code-block:: text

   GET https://{endpoint}/v2/{project_id}/groups

   /v2/{project_id}/groups

Example Responses
-----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
     "log_groups" : [ {
       "creation_time" : 1630547141853,
       "log_group_name" : "lts-group-01nh",
       "log_group_id" : "b6b9332b-091f-4b22-b810-264318d2d664",
       "ttl_in_days" : 7
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
