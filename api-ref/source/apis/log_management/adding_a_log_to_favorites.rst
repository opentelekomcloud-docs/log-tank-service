:original_name: Createfavorite.html

.. _Createfavorite:

Adding a Log to Favorites
=========================

Function
--------

This API is used to add a log to favorites.

URI
---

POST /v1.0/{project_id}/lts/favorite

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

   +--------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                   |
   +==============+===========+========+===============================================================================================================================+
   | X-Auth-Token | Yes       | String | User token obtained from IAM. For details about how to obtain a user token, see :ref:`Obtaining a User Token <lts_api_0004>`. |
   +--------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type | Yes       | String | Set this parameter to **application/json;charset=utf8**.                                                                      |
   +--------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Parameter              | Mandatory       | Type            | Description                                                                                                                   |
   +========================+=================+=================+===============================================================================================================================+
   | eps_id                 | No              | String          | Enterprise project ID.                                                                                                        |
   +------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
   | favorite_resource_id   | Yes             | String          | Favorite resource ID.                                                                                                         |
   +------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
   | favorite_resource_type | Yes             | String          | Favorite resource type.                                                                                                       |
   |                        |                 |                 |                                                                                                                               |
   |                        |                 |                 | -  **LOG_STREAM**                                                                                                             |
   |                        |                 |                 |                                                                                                                               |
   |                        |                 |                 | -  **LOG_GROUP**                                                                                                              |
   +------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
   | log_group_id           | Yes             | String          | Log group ID.                                                                                                                 |
   +------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
   | log_group_name         | No              | String          | Log group name.                                                                                                               |
   +------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
   | log_stream_id          | Yes             | String          | Log stream ID.                                                                                                                |
   +------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
   | log_stream_name        | No              | String          | Log stream name.                                                                                                              |
   +------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
   | is_global              | Yes             | Boolean         | Whether global favorites are supported. This parameter must be set to **true**. Otherwise, logs cannot be added to favorites. |
   +------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 4** Response body parameters

   +------------------------+---------+------------------------------------------------------------------------+
   | Parameter              | Type    | Description                                                            |
   +========================+=========+========================================================================+
   | create_time            | Integer | Creation time.                                                         |
   +------------------------+---------+------------------------------------------------------------------------+
   | eps_id                 | String  | Enterprise project ID.                                                 |
   +------------------------+---------+------------------------------------------------------------------------+
   | favorite_resource_id   | String  | Favorite resource ID.                                                  |
   +------------------------+---------+------------------------------------------------------------------------+
   | favorite_resource_type | String  | Favorite resource type.                                                |
   +------------------------+---------+------------------------------------------------------------------------+
   | log_group_id           | String  | Log group ID.                                                          |
   +------------------------+---------+------------------------------------------------------------------------+
   | log_group_name         | String  | Log group name.                                                        |
   +------------------------+---------+------------------------------------------------------------------------+
   | log_stream_id          | String  | Log stream ID.                                                         |
   +------------------------+---------+------------------------------------------------------------------------+
   | log_stream_name        | String  | Log stream name.                                                       |
   +------------------------+---------+------------------------------------------------------------------------+
   | project_id             | String  | Project ID.                                                            |
   +------------------------+---------+------------------------------------------------------------------------+
   | is_global              | Boolean | Whether to enable the function of adding logs to favorites.            |
   +------------------------+---------+------------------------------------------------------------------------+
   | log_group_name_alias   | String  | Log group alias, which is the same as the log group name by default.   |
   +------------------------+---------+------------------------------------------------------------------------+
   | log_stream_name_alias  | String  | Log stream alias, which is the same as the log stream name by default. |
   +------------------------+---------+------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 5** Response body parameters

   +-----------+----------------------------------------------------------------------------+---------------------+
   | Parameter | Type                                                                       | Description         |
   +===========+============================================================================+=====================+
   | message   | :ref:`ErrorMessagebody <createfavorite__response_errormessagebody>` object | Error message body. |
   +-----------+----------------------------------------------------------------------------+---------------------+

.. _createfavorite__response_errormessagebody:

.. table:: **Table 6** ErrorMessagebody

   ========= ====== ==============
   Parameter Type   Description
   ========= ====== ==============
   code      String Error code.
   details   String Error message.
   ========= ====== ==============

**Status code: 500**

.. table:: **Table 7** Response body parameters

   +-----------+------------------------------------------------------------------------------+---------------------+
   | Parameter | Type                                                                         | Description         |
   +===========+==============================================================================+=====================+
   | message   | :ref:`ErrorMessagebody <createfavorite__response_errormessagebody_1>` object | Error message body. |
   +-----------+------------------------------------------------------------------------------+---------------------+

.. _createfavorite__response_errormessagebody_1:

.. table:: **Table 8** ErrorMessagebody

   ========= ====== ==============
   Parameter Type   Description
   ========= ====== ==============
   code      String Error code.
   details   String Error message.
   ========= ====== ==============

Example Requests
----------------

Adding a Log to Favorites

.. code-block:: text

   POST /v1.0/2a473356cca5487f8373be891bffc1cf/lts/favorite

   {
     "log_group_id" : "d91fff37-9d10-47f1-85de-c2840724908f",
     "log_group_name" : "lts-group-sgq1",
     "log_stream_id" : "f2fb0a2d-d4cd-4bc9-ac12-93c6d255883c",
     "log_stream_name" : "lts-topic-xxxxtest",
     "eps_id" : "0",
     "favorite_resource_id" : "f2fb0a2d-d4cd-4bc9-ac12-93c6d255883c",
     "favorite_resource_type" : "log_stream",
     "is_global" : true
   }

Example Responses
-----------------

**Status code: 201**

A log is added to favorites.

.. code-block::

   {
     "create_time" : 1669018970929,
     "eps_id" : "0",
     "favorite_resource_id" : "f2fb0a2d-d4cd-4bc9-ac12-93c6d255883c",
     "is_global" : true,
     "favorite_resource_type" : "LOG_STREAM",
     "log_group_id" : "d91fff37-9d10-47f1-85de-c2840724908f",
     "log_group_name" : "lts-group-sgq1",
     "log_stream_id" : "f2fb0a2d-d4cd-4bc9-ac12-93c6d255883c",
     "log_stream_name" : "lts-topic-xxxxtest",
     "project_id" : "2a473356cca5487f8373be891bffc1cf"
   }

**Status code: 400**

Invalid request. Modify the request based on the description in **error_msg** before a retry.

.. code-block::

   {
     "message" : {
       "code" : "LTS.0603",
       "details" : "group or stream not exist"
     }
   }

**Status code: 500**

The server has received the request but encountered an internal error.

.. code-block::

   {
     "message" : {
       "code" : "LTS.0203",
       "details" : "Internal Server Error"
     }
   }

Status Codes
------------

+-------------+-----------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                   |
+=============+===============================================================================================+
| 201         | A log is added to favorites.                                                                  |
+-------------+-----------------------------------------------------------------------------------------------+
| 400         | Invalid request. Modify the request based on the description in **error_msg** before a retry. |
+-------------+-----------------------------------------------------------------------------------------------+
| 500         | The server has received the request but encountered an internal error.                        |
+-------------+-----------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
