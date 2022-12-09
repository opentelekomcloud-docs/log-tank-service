:original_name: lts_api_0027.html

.. _lts_api_0027:

Creating a Log Transfer Task
============================

Function
--------

This API is used to transfer logs of one or more specified log streams to Object Storage Service (OBS).

URI
---

POST /v2/{project_id}/log-dump/obs

.. table:: **Table 1** URI parameter

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                         |
   +=================+=================+=================+=====================================================================================================================================================+
   | project_id      | Yes             | String          | Project ID. For details about how to obtain the ID, see :ref:`Obtaining the AccountID, Project ID, Log Group ID, and Log Stream ID <lts_api_0006>`. |
   |                 |                 |                 |                                                                                                                                                     |
   |                 |                 |                 | Default value: None                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                     |
   |                 |                 |                 | Value length: 32 characters                                                                                                                         |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                               |
   +=================+=================+=================+===========================================================+
   | X-Auth-Token    | Yes             | String          | User token obtained from IAM.                             |
   |                 |                 |                 |                                                           |
   |                 |                 |                 | Default value: None                                       |
   |                 |                 |                 |                                                           |
   |                 |                 |                 | Minimum length: 1000 characters                           |
   |                 |                 |                 |                                                           |
   |                 |                 |                 | Maximum length: 2000 characters                           |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------+
   | Content-Type    | Yes             | String          | Set this parameter to **application/json;charset=UTF-8**. |
   |                 |                 |                 |                                                           |
   |                 |                 |                 | Default value: None                                       |
   |                 |                 |                 |                                                           |
   |                 |                 |                 | Minimum length: 30 characters                             |
   |                 |                 |                 |                                                           |
   |                 |                 |                 | Maximum length: 30 characters                             |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                                                          |
   +=================+=================+==================+======================================================================================================================================================================================================================+
   | log_group_id    | Yes             | String           | Log group ID.                                                                                                                                                                                                        |
   |                 |                 |                  |                                                                                                                                                                                                                      |
   |                 |                 |                  | Value length: 36 characters                                                                                                                                                                                          |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_stream_ids  | Yes             | Array of strings | Indicates IDs of log streams whose logs are to be periodically transferred to OBS. You can specify one or more log streams.                                                                                          |
   |                 |                 |                  |                                                                                                                                                                                                                      |
   |                 |                 |                  | Example value:                                                                                                                                                                                                       |
   |                 |                 |                  |                                                                                                                                                                                                                      |
   |                 |                 |                  | -  7bb6b1e7-xxxx-4255-87f9-b3dc7fb2xxxx                                                                                                                                                                              |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | obs_bucket_name | Yes             | String           | Indicates the name of an OBS bucket.                                                                                                                                                                                 |
   |                 |                 |                  |                                                                                                                                                                                                                      |
   |                 |                 |                  | Minimum length: 3 characters                                                                                                                                                                                         |
   |                 |                 |                  |                                                                                                                                                                                                                      |
   |                 |                 |                  | Maximum length: 63 characters                                                                                                                                                                                        |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type            | Yes             | String           | Set this parameter to **cycle**, which indicates that the log transfer is periodic.                                                                                                                                  |
   |                 |                 |                  |                                                                                                                                                                                                                      |
   |                 |                 |                  | Value length: 5 characters                                                                                                                                                                                           |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | storage_format  | Yes             | String           | Indicates whether the logs are stored in raw or JSON format. The default value is **RAW**.                                                                                                                           |
   |                 |                 |                  |                                                                                                                                                                                                                      |
   |                 |                 |                  | Minimum length: 3 characters                                                                                                                                                                                         |
   |                 |                 |                  |                                                                                                                                                                                                                      |
   |                 |                 |                  | Maximum length: 4 characters                                                                                                                                                                                         |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | switch_on       | No              | Boolean          | Indicates whether the log transfer is enabled. The value is **true** (default) or **false**.                                                                                                                         |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | prefix_name     | No              | String           | Indicates the file name prefix of the log files transferred to an OBS bucket.                                                                                                                                        |
   |                 |                 |                  |                                                                                                                                                                                                                      |
   |                 |                 |                  | Minimum length: 0 characters                                                                                                                                                                                         |
   |                 |                 |                  |                                                                                                                                                                                                                      |
   |                 |                 |                  | Maximum length: 64 characters                                                                                                                                                                                        |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dir_prefix_name | No              | String           | Indicates a custom path to store the log files.                                                                                                                                                                      |
   |                 |                 |                  |                                                                                                                                                                                                                      |
   |                 |                 |                  | Minimum length: 0 characters                                                                                                                                                                                         |
   |                 |                 |                  |                                                                                                                                                                                                                      |
   |                 |                 |                  | Maximum length: 64 characters                                                                                                                                                                                        |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | period          | Yes             | Integer          | Indicates the length of the log transfer interval.                                                                                                                                                                   |
   |                 |                 |                  |                                                                                                                                                                                                                      |
   |                 |                 |                  | Example values: **1**, **2**, **3**, **5**, **6**, **12**, and **30**                                                                                                                                                |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | period_unit     | Yes             | String           | Indicates the unit of the log transfer interval.                                                                                                                                                                     |
   |                 |                 |                  |                                                                                                                                                                                                                      |
   |                 |                 |                  | Example values: **min** and **hour**                                                                                                                                                                                 |
   |                 |                 |                  |                                                                                                                                                                                                                      |
   |                 |                 |                  | Minimum length: 3 characters                                                                                                                                                                                         |
   |                 |                 |                  |                                                                                                                                                                                                                      |
   |                 |                 |                  | Maximum length: 4 characters                                                                                                                                                                                         |
   |                 |                 |                  |                                                                                                                                                                                                                      |
   |                 |                 |                  | .. note::                                                                                                                                                                                                            |
   |                 |                 |                  |                                                                                                                                                                                                                      |
   |                 |                 |                  |    The log transfer interval is specified by the combination of the values of **period** and **period_unit**, and must be set to one of the following: 2 min, 5 min, 30 min, 1 hour, 3 hours, 6 hours, and 12 hours. |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 4** Response body parameter

   +-----------------------+-----------------------+-----------------------------+
   | Parameter             | Type                  | Description                 |
   +=======================+=======================+=============================+
   | log_dump_obs_id       | String                | Transfer task ID.           |
   |                       |                       |                             |
   |                       |                       | Default value: None         |
   |                       |                       |                             |
   |                       |                       | Value length: 36 characters |
   +-----------------------+-----------------------+-----------------------------+

**Status code: 400**

.. table:: **Table 5** Response body parameters

   +-----------------------+-----------------------+-----------------------------------------+
   | Parameter             | Type                  | Description                             |
   +=======================+=======================+=========================================+
   | error_code            | String                | Error code.                             |
   |                       |                       |                                         |
   |                       |                       | Example value:                          |
   |                       |                       |                                         |
   |                       |                       | -  LTS.0007                             |
   +-----------------------+-----------------------+-----------------------------------------+
   | error_msg             | String                | Error message.                          |
   |                       |                       |                                         |
   |                       |                       | Example value:                          |
   |                       |                       |                                         |
   |                       |                       | -  The request body format must be json |
   +-----------------------+-----------------------+-----------------------------------------+

**Status code: 403**

.. table:: **Table 6** Response body parameters

   +-----------------------+-----------------------+-----------------------+
   | Parameter             | Type                  | Description           |
   +=======================+=======================+=======================+
   | error_code            | String                | Error code.           |
   |                       |                       |                       |
   |                       |                       | Example value:        |
   |                       |                       |                       |
   |                       |                       | -  LTS.0403           |
   +-----------------------+-----------------------+-----------------------+
   | error_msg             | String                | Error message.        |
   |                       |                       |                       |
   |                       |                       | Example value:        |
   |                       |                       |                       |
   |                       |                       | -  Invalid projectId  |
   +-----------------------+-----------------------+-----------------------+

**Status code: 500**

.. table:: **Table 7** Response body parameters

   +-----------------------+-----------------------+-----------------------+
   | Parameter             | Type                  | Description           |
   +=======================+=======================+=======================+
   | error_code            | String                | Error code.           |
   |                       |                       |                       |
   |                       |                       | Example value:        |
   |                       |                       |                       |
   |                       |                       | -  LTS.0403           |
   +-----------------------+-----------------------+-----------------------+
   | error_msg             | String                | Error message.        |
   |                       |                       |                       |
   |                       |                       | Example value:        |
   |                       |                       |                       |
   |                       |                       | -  Invalid projectId  |
   +-----------------------+-----------------------+-----------------------+

Example Request
---------------

.. code-block:: text

   POST https://{endpoint}/v2/{project_id}/log-dump/obs

   /v2/{project_id}/log-dump/obs
   {
     "log_group_id": "d9dba9f3-xxxx-48bd-xxxx-xxxxa24a8053",
     "log_stream_ids": ["45e7f609-xxxx-4cd3-835b-xxxx4a124718"],
     "obs_bucket_name": "lts-test",
     "type": "cycle",
     "storage_format": "RAW",
     "switch_on": "true",
     "prefix_name": "fileprefixname",
     "dir_prefix_name": "dirprefixname",
     "period": 5,
     "period_unit": "min"
   }

Example Response
----------------

**Status code: 200**

-  The log group does not exist.

   .. code-block::

      {
        "error_code": "LTS.0201",
        "error_msg": "The log group does not existed"
      }

-  The log stream does not exist.

   .. code-block::

      {
        "error_code": "LTS.0208",
        "error_msg": "Log stream id does not exist: 632b9bdc-5afd-4666-a5de-2579f8b80314-"
      }

-  The OBS bucket does not exist.

   .. code-block::

      {
        "error_code": "LTS.0416",
        "error_msg": "obs bucket does not exist: zhuanchu"
      }

-  The log stream ID has been associated with a transfer task.

   .. code-block::

      {
        "error_code": "LTS.0207",
        "error_msg": "Log stream id is associated by transfer: 632b9bdc-5afd-4666-a5de-2579f8b80314"
      }

-  Invalid transfer type.

   .. code-block::

      {
        "error_code": "LTS.1901",
        "error_msg": "type is not in the list [cycle]"
      }

-  Invalid storage format.

   .. code-block::

      {
        "error_code": "LTS.1901",
        "error_msg": "storage_format is not in the list [RAW, JSON]"
      }

-  Invalid log transfer interval.

   .. code-block::

      {
        "error_code": "LTS.1901",
        "error_msg": "period+period_unit is not in the list [2min, 5min, 30min, 1hour, 3hour, 6hour, 12hour]"
      }

-  Invalid unit of the log transfer interval.

   .. code-block::

      {
        "error_code": "LTS.1901",
        "error_msg": "period_unit is not in the list [min, hour]"
      }

-  Invalid file name prefix.

   .. code-block::

      {
         "error_code": "LTS.1902",
         "error_msg": "prefix_name is invalid, please verify if it's provided as required"
      }

-  Invalid custom path to store log files.

   .. code-block::

      {
        "error_code": "LTS.1902",
        "error_msg": "dir_prefix_name is invalid, please verify if it's provided as required"
      }

**Status code: 201**

.. code-block::

   {
     "log_dump_obs_id" : "45fdc36b-xxxx-4567-xxxx-559xxxxdf968"
   }

**Status code: 400**

-  The request is invalid. Modify the request based on the description in **error_msg** before a retry.

   .. code-block::

      {
        "error_code" : "LTS.0009",
        "error_msg" : "Failed to validate the request body"
      }

-  The request is invalid. Modify the request based on the description in **error_msg** before a retry.

   .. code-block::

      {
        "error_code": "LTS.0007",
        "error_msg": "The request body format must be json"
      }

**Status code: 403**

The server understood the request but refused to authorize it. The client should not repeat the request without modifications.

.. code-block::

   {
     "error_code" : "LTS.0001",
     "error_msg" : "Invalid projectId"
   }

**Status code: 500**

-  The server has received the request but encountered an internal error.

   .. code-block::

      {
        "error_code" : "LTS.0202",
        "error_msg" : "Failed to query lts struct log"
      }

-  The server has received the request but encountered an internal error.

   .. code-block::

      {
        "error_code": "LTS.0010",
        "error_msg": "Internal Server Error"
      }

Status Codes
------------

+-------------+--------------------------------------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                                                    |
+=============+================================================================================================================================+
| 200         | The request has succeeded.                                                                                                     |
+-------------+--------------------------------------------------------------------------------------------------------------------------------+
| 201         | The request has succeeded. The transfer task has been created.                                                                 |
+-------------+--------------------------------------------------------------------------------------------------------------------------------+
| 400         | The request is invalid. Modify the request based on the description in **error_msg** before a retry.                           |
+-------------+--------------------------------------------------------------------------------------------------------------------------------+
| 403         | The server understood the request but refused to authorize it. The client should not repeat the request without modifications. |
+-------------+--------------------------------------------------------------------------------------------------------------------------------+
| 500         | The server has received the request but encountered an internal error.                                                         |
+-------------+--------------------------------------------------------------------------------------------------------------------------------+
| 503         | The requested service is unavailable.                                                                                          |
+-------------+--------------------------------------------------------------------------------------------------------------------------------+

Error Codes
-----------

For details, see :ref:`Error Codes <lts_02_0021>`.
