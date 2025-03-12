:original_name: CreateLogStream.html

.. _CreateLogStream:

Creating a Log Stream
=====================

Function
--------

This API is used to create a log stream in a specified log group.

URI
---

POST /v2/{project_id}/groups/{log_group_id}/streams

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

.. table:: **Table 3** Request body parameters

   +-------------------------+-----------------+----------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter               | Mandatory       | Type                                                                 | Description                                                                                                                               |
   +=========================+=================+======================================================================+===========================================================================================================================================+
   | log_stream_name         | Yes             | String                                                               | Name of the log stream to be created.                                                                                                     |
   |                         |                 |                                                                      |                                                                                                                                           |
   |                         |                 |                                                                      | Minimum: **1**                                                                                                                            |
   |                         |                 |                                                                      |                                                                                                                                           |
   |                         |                 |                                                                      | Maximum: **64**                                                                                                                           |
   +-------------------------+-----------------+----------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
   | ttl_in_days             | No              | Integer                                                              | Log retention duration.                                                                                                                   |
   |                         |                 |                                                                      |                                                                                                                                           |
   |                         |                 |                                                                      | Minimum value: **1**                                                                                                                      |
   |                         |                 |                                                                      |                                                                                                                                           |
   |                         |                 |                                                                      | Maximum value: **365**                                                                                                                    |
   +-------------------------+-----------------+----------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                    | No              | Array of :ref:`tagsBody <createlogstream__request_tagsbody>` objects | Tag field information.                                                                                                                    |
   +-------------------------+-----------------+----------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
   | log_stream_name_alias   | No              | String                                                               | Log stream alias.                                                                                                                         |
   |                         |                 |                                                                      |                                                                                                                                           |
   |                         |                 |                                                                      | Minimum: **1**                                                                                                                            |
   |                         |                 |                                                                      |                                                                                                                                           |
   |                         |                 |                                                                      | Maximum: **64**                                                                                                                           |
   +-------------------------+-----------------+----------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_name | No              | String                                                               | Enterprise project name.                                                                                                                  |
   |                         |                 |                                                                      |                                                                                                                                           |
   |                         |                 |                                                                      | .. note::                                                                                                                                 |
   |                         |                 |                                                                      |                                                                                                                                           |
   |                         |                 |                                                                      |    A project name can only contain letters, digits, underscores (_), and hyphens (-). It cannot contain the word **default** in any form. |
   |                         |                 |                                                                      |                                                                                                                                           |
   |                         |                 |                                                                      |    The description can contain up to 512 characters.                                                                                      |
   |                         |                 |                                                                      |                                                                                                                                           |
   |                         |                 |                                                                      | Minimum: **1**                                                                                                                            |
   |                         |                 |                                                                      |                                                                                                                                           |
   |                         |                 |                                                                      | Maximum: **255**                                                                                                                          |
   +-------------------------+-----------------+----------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+

.. _createlogstream__request_tagsbody:

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

   ============= ====== =============================
   Parameter     Type   Description
   ============= ====== =============================
   log_stream_id String ID of the created log stream.
   ============= ====== =============================

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

Creating a log stream

.. code-block:: text

   POST https://{endpoint}/v2/{project_id}/groups/{log_group_id}/streams

   {
     "log_stream_name" : "lts-stream-02kh"
   }

Example Responses
-----------------

**Status code: 201**

The request is successful and the log stream has been created.

.. code-block::

   {
     "log_stream_id" : "c54dbc58-0fd8-48ed-b007-6d54981427a7"
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
     "error_code" : "LTS.0202",
     "error_msg" : "Failed to create Log stream"
   }

Status Codes
------------

+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Status Code                       | Description                                                                                                                                                                                  |
+===================================+==============================================================================================================================================================================================+
| 201                               | The request is successful and the log stream has been created.                                                                                                                               |
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
