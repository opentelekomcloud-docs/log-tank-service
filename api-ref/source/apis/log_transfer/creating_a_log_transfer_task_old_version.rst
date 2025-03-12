:original_name: lts_api_0029.html

.. _lts_api_0029:

Creating a Log Transfer Task (Old Version)
==========================================

Function
--------

This API is used to transfer logs of one or more specified log streams to Object Storage Service (OBS).

URI
---

POST /v2/{project_id}/log-dump/obs

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

   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                               |
   +=================+=================+==================+===========================================================================================================================================================================================+
   | log_group_id    | Yes             | String           | Log group ID.                                                                                                                                                                             |
   |                 |                 |                  |                                                                                                                                                                                           |
   |                 |                 |                  | Minimum: **36**                                                                                                                                                                           |
   |                 |                 |                  |                                                                                                                                                                                           |
   |                 |                 |                  | Maximum: **36**                                                                                                                                                                           |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_stream_ids  | Yes             | Array of strings | Indicates IDs of log streams whose logs are to be periodically transferred to OBS. You can specify one or more log streams.                                                               |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | obs_bucket_name | Yes             | String           | Name of an OBS bucket.                                                                                                                                                                    |
   |                 |                 |                  |                                                                                                                                                                                           |
   |                 |                 |                  | Minimum: **3**                                                                                                                                                                            |
   |                 |                 |                  |                                                                                                                                                                                           |
   |                 |                 |                  | Maximum: **63**                                                                                                                                                                           |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type            | Yes             | String           | Set this parameter to **cycle**, which indicates that the log transfer is periodic.                                                                                                       |
   |                 |                 |                  |                                                                                                                                                                                           |
   |                 |                 |                  | Minimum: **5**                                                                                                                                                                            |
   |                 |                 |                  |                                                                                                                                                                                           |
   |                 |                 |                  | Maximum: **5**                                                                                                                                                                            |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | storage_format  | Yes             | String           | Whether the logs are stored in raw or JSON format. The default value is **RAW**.                                                                                                          |
   |                 |                 |                  |                                                                                                                                                                                           |
   |                 |                 |                  | Minimum length: 3 characters.                                                                                                                                                             |
   |                 |                 |                  |                                                                                                                                                                                           |
   |                 |                 |                  | Maximum length: 4 characters.                                                                                                                                                             |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | switch_on       | No              | Boolean          | Whether log transfer is enabled. The value is **true** (default) or **false**.                                                                                                            |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | prefix_name     | No              | String           | The file name prefix of the log files transferred to an OBS bucket.                                                                                                                       |
   |                 |                 |                  |                                                                                                                                                                                           |
   |                 |                 |                  | Minimum: **0**                                                                                                                                                                            |
   |                 |                 |                  |                                                                                                                                                                                           |
   |                 |                 |                  | Maximum: **64**                                                                                                                                                                           |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dir_prefix_name | No              | String           | A custom path to store the log files.                                                                                                                                                     |
   |                 |                 |                  |                                                                                                                                                                                           |
   |                 |                 |                  | Minimum: **0**                                                                                                                                                                            |
   |                 |                 |                  |                                                                                                                                                                                           |
   |                 |                 |                  | Maximum: **64**                                                                                                                                                                           |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | period          | Yes             | Integer          | Length of the log transfer interval.                                                                                                                                                      |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | period_unit     | Yes             | String           | Unit of the log transfer interval.>The combination of **period** and **period_unit** must be one of ["**2min**","**5min**","**30min**","**1hour**","**3hour**","**6hour**","**12hour**"]. |
   |                 |                 |                  |                                                                                                                                                                                           |
   |                 |                 |                  | Minimum: **3**                                                                                                                                                                            |
   |                 |                 |                  |                                                                                                                                                                                           |
   |                 |                 |                  | Maximum: **4**                                                                                                                                                                            |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 4** Response body parameters

   =============== ====== =================
   Parameter       Type   Description
   =============== ====== =================
   log_dump_obs_id String Transfer task ID.
   =============== ====== =================

**Status code: 400**

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

Creating a log transfer task

.. code-block:: text

   POST https://{endpoint}/v2/{project_id}/log-dump/obs

   {
     "log_group_id" : "d9dba9f3-xxxx-48bd-xxxx-xxxxa24a8053",
     "log_stream_ids" : [ "45e7f609-xxxx-4cd3-835b-xxxx4a124718" ],
     "obs_bucket_name" : "lts-test",
     "type" : "cycle",
     "storage_format" : "RAW",
     "switch_on" : "true",
     "prefix_name" : "fileprefixname",
     "dir_prefix_name" : "dirprefixname",
     "period" : 5,
     "period_unit" : "min"
   }

Example Responses
-----------------

**Status code: 200**

The request is successful.

-  The log group does not exist.

   .. code-block::

      {
        "error_code" : "LTS.0201",
        "error_msg" : "The log group does not existed"
      }

-  The log stream does not exist.

   .. code-block::

      {
        "error_code" : "LTS.0208",
        "error_msg" : "Log stream id does not exist: 632b9bdc-5afd-4666-a5de-2579f8b80314-"
      }

-  The OBS bucket does not exist.

   .. code-block::

      {
        "error_code" : "LTS.0416",
        "error_msg" : "obs bucket does not exist: zhuanchu"
      }

-  The log stream ID has been associated during log transfer.

   .. code-block::

      {
        "error_code" : "LTS.0207",
        "error_msg" : "Log stream id is associated by transfer: 632b9bdc-5afd-4666-a5de-2579f8b80314"
      }

-  The transfer type is not in the list.

   .. code-block::

      {
        "error_code" : "LTS.1901",
        "error_msg" : "type is not in the list [cycle]"
      }

-  The transfer format is not in the list.

   .. code-block::

      {
        "error_code" : "LTS.1901",
        "error_msg" : "storage_format is not in the list [RAW, JSON]"
      }

-  The transfer interval is not in the list.

   .. code-block::

      {
        "error_code" : "LTS.1901",
        "error_msg" : "period+period_unit is not in the list [2min, 5min, 30min, 1hour, 3hour, 6hour, 12hour]"
      }

-  The transfer unit is not in the list.

   .. code-block::

      {
        "error_code" : "LTS.1901",
        "error_msg" : "period_unit is not in the list [min, hour]"
      }

-  The prefix of the transferred log file is invalid. Check the prefix.

   .. code-block::

      {
        "error_code" : "LTS.1902",
        "error_msg" : "prefix_name is invalid, please verify if it's provided as required"
      }

-  The prefix of the custom transfer path is invalid. Check the prefix.

   .. code-block::

      {
        "error_code" : "LTS.1902",
        "error_msg" : "dir_prefix_name is invalid, please verify if it's provided as required"
      }

**Status code: 201**

The request is successful.

.. code-block::

   {
     "log_dump_obs_id" : "45fdc36b-xxxx-4567-xxxx-559xxxxdf968"
   }

**Status code: 400**

BadRequest. The request is invalid. Modify the request based on the description in **error_msg** before a retry.

.. code-block::

   BadRequest. The request is invalid. Modify the request based on the description in **error_msg** before a retry.
   {
     "error_code": "LTS.0007",
     "error_msg": "The request body format must be json"
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

   InternalServerError. The server has received the request but encountered an internal error.
   {
     "error_code": "LTS.0010",
     "error_msg": "Internal Server Error"}

Status Codes
------------

+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Status Code                       | Description                                                                                                                                                                                  |
+===================================+==============================================================================================================================================================================================+
| 200                               | The request is successful.                                                                                                                                                                   |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 201                               | The request is successful.                                                                                                                                                                   |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 400                               | BadRequest. The request is invalid. Modify the request based on the description in **error_msg** before a retry.                                                                             |
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
