:original_name: lts_api_0012.html

.. _lts_api_0012:

Creating a Log Group
====================

Function
--------

This API is used to create a log group for log retention and query. You can create a maximum of 100 log groups.

URI
---

POST /v2/{project_id}/groups

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
   |                 |                 |                 | Length: 30 characters                                     |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                        |
   +=================+=================+=================+====================================================+
   | log_group_name  | Yes             | String          | Name of the log group to be created.               |
   |                 |                 |                 |                                                    |
   |                 |                 |                 | Minimum length: 1 character                        |
   |                 |                 |                 |                                                    |
   |                 |                 |                 | Maximum length: 64 characters                      |
   |                 |                 |                 |                                                    |
   |                 |                 |                 | Enumerated value:                                  |
   |                 |                 |                 |                                                    |
   |                 |                 |                 | -  **lts-group-01nh**                              |
   +-----------------+-----------------+-----------------+----------------------------------------------------+
   | ttl_in_days     | Yes             | Integer         | Log retention duration, in days (fixed to 7 days). |
   +-----------------+-----------------+-----------------+----------------------------------------------------+

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 4** Response body parameter

   +-----------------------+-----------------------+------------------------------+
   | Parameter             | Type                  | Description                  |
   +=======================+=======================+==============================+
   | log_group_id          | String                | ID of the created log group. |
   |                       |                       |                              |
   |                       |                       | Value length: 36 characters  |
   +-----------------------+-----------------------+------------------------------+

**Status code: 400**

.. table:: **Table 5** Response body parameters

   +-----------------------+-----------------------+--------------------------+
   | Parameter             | Type                  | Description              |
   +=======================+=======================+==========================+
   | error_code            | String                | Error code.              |
   |                       |                       |                          |
   |                       |                       | Enumerated value:        |
   |                       |                       |                          |
   |                       |                       | -  **LTS.0403**          |
   +-----------------------+-----------------------+--------------------------+
   | error_msg             | String                | Error message.           |
   |                       |                       |                          |
   |                       |                       | Enumerated value:        |
   |                       |                       |                          |
   |                       |                       | -  **Invalid projectId** |
   +-----------------------+-----------------------+--------------------------+

**Status code: 401**

.. table:: **Table 6** Response body parameters

   +-----------------------+-----------------------+--------------------------+
   | Parameter             | Type                  | Description              |
   +=======================+=======================+==========================+
   | error_code            | String                | Error code.              |
   |                       |                       |                          |
   |                       |                       | Enumerated value:        |
   |                       |                       |                          |
   |                       |                       | -  **LTS.0403**          |
   +-----------------------+-----------------------+--------------------------+
   | error_msg             | String                | Error message.           |
   |                       |                       |                          |
   |                       |                       | Enumerated value:        |
   |                       |                       |                          |
   |                       |                       | -  **Invalid projectId** |
   +-----------------------+-----------------------+--------------------------+

**Status code: 403**

.. table:: **Table 7** Response body parameters

   +-----------------------+-----------------------+--------------------------+
   | Parameter             | Type                  | Description              |
   +=======================+=======================+==========================+
   | error_code            | String                | Error code.              |
   |                       |                       |                          |
   |                       |                       | Enumerated value:        |
   |                       |                       |                          |
   |                       |                       | -  **LTS.0403**          |
   +-----------------------+-----------------------+--------------------------+
   | error_msg             | String                | Error message.           |
   |                       |                       |                          |
   |                       |                       | Enumerated value:        |
   |                       |                       |                          |
   |                       |                       | -  **Invalid projectId** |
   +-----------------------+-----------------------+--------------------------+

**Status code: 500**

.. table:: **Table 8** Response body parameters

   +-----------------------+-----------------------+--------------------------+
   | Parameter             | Type                  | Description              |
   +=======================+=======================+==========================+
   | error_code            | String                | Error code.              |
   |                       |                       |                          |
   |                       |                       | Enumerated value:        |
   |                       |                       |                          |
   |                       |                       | -  **LTS.0403**          |
   +-----------------------+-----------------------+--------------------------+
   | error_msg             | String                | Error message.           |
   |                       |                       |                          |
   |                       |                       | Enumerated value:        |
   |                       |                       |                          |
   |                       |                       | -  **Invalid projectId** |
   +-----------------------+-----------------------+--------------------------+

**Status code: 503**

.. table:: **Table 9** Response body parameters

   +-----------------------+-----------------------+--------------------------+
   | Parameter             | Type                  | Description              |
   +=======================+=======================+==========================+
   | error_code            | String                | Error code.              |
   |                       |                       |                          |
   |                       |                       | Enumerated value:        |
   |                       |                       |                          |
   |                       |                       | -  **LTS.0403**          |
   +-----------------------+-----------------------+--------------------------+
   | error_msg             | String                | Error message.           |
   |                       |                       |                          |
   |                       |                       | Enumerated value:        |
   |                       |                       |                          |
   |                       |                       | -  **Invalid projectId** |
   +-----------------------+-----------------------+--------------------------+

Example Request
---------------

.. code-block:: text

   POST https://{endpoint}/v2/{project_id}/groups

   /v2/{project_id}/groups
   {
     "log_group_name": "lts-group-01nh",
     "ttl_in_days": 7
   }

Example Response
----------------

**Status code: 201**

.. code-block::

   {
     "log_group_id":"b6b9332b-091f-4b22-b810-264318d2d664"
   }

**Status code: 400**

The request is invalid. Modify the request based on the description in **error_msg** before a retry.

.. code-block::

   {
     "error_code" : "LTS.0009",
     "error_msg" : "Failed to validate the request body"
   }

**Status code: 401**

Authentication failed. Check the token and try again.

.. code-block::

   {
     "error_code" : "LTS.0003",
     "error_msg" : "Invalid token"
   }

**Status code: 403**

The server understood the request but refused to authorize it. The client should not repeat the request without modifications.

.. code-block::

   {
     "error_code" : "LTS.0001",
     "error_msg" : "Invalid projectId"
   }

**Status code: 500**

The server has received the request but encountered an internal error.

.. code-block::

   {
     "error_code" : "LTS.0102",
     "error_msg" : "Failed to create log group"
   }

Status Codes
------------

+-------------+--------------------------------------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                                                    |
+=============+================================================================================================================================+
| 201         | The request has succeeded and the log group has been created.                                                                  |
+-------------+--------------------------------------------------------------------------------------------------------------------------------+
| 400         | The request is invalid. Modify the request based on the description in **error_msg** before a retry.                           |
+-------------+--------------------------------------------------------------------------------------------------------------------------------+
| 401         | Authentication failed. Check the token and try again.                                                                          |
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
