:original_name: lts_api_0024.html

.. _lts_api_0024:

Modifying a Log Group
=====================

Function
--------

This API is used to modify the log retention duration of a specified log group.

URI
---

POST /v2/{project_id}/groups/{log_group_id}

.. table:: **Table 1** URI parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                   |
   +=================+=================+=================+===============================================================================================================================================================+
   | project_id      | Yes             | String          | Project ID. For details about how to obtain a project ID, see :ref:`Obtaining the AccountID, Project ID, Log Group ID, and Log Stream ID <lts_api_0006>`.     |
   |                 |                 |                 |                                                                                                                                                               |
   |                 |                 |                 | Default value: None                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                               |
   |                 |                 |                 | Value length: 36 characters                                                                                                                                   |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_group_id    | Yes             | String          | Log group ID. For details about how to obtain a log group ID, see :ref:`Obtaining the AccountID, Project ID, Log Group ID, and Log Stream ID <lts_api_0006>`. |
   |                 |                 |                 |                                                                                                                                                               |
   |                 |                 |                 | Default value: None                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                               |
   |                 |                 |                 | Value length: 36 characters                                                                                                                                   |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

.. table:: **Table 3** Request body parameter

   +-------------+-----------+---------+----------------------------------------------------+
   | Parameter   | Mandatory | Type    | Description                                        |
   +=============+===========+=========+====================================================+
   | ttl_in_days | Yes       | Integer | Log retention duration, in days (fixed to 7 days). |
   +-------------+-----------+---------+----------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------------------+-----------------------+----------------------------------------------------+
   | Parameter             | Type                  | Description                                        |
   +=======================+=======================+====================================================+
   | creation_time         | long                  | Time when a log group was created.                 |
   +-----------------------+-----------------------+----------------------------------------------------+
   | log_group_name        | String                | Log group name.                                    |
   |                       |                       |                                                    |
   |                       |                       | Minimum length: 1 character                        |
   |                       |                       |                                                    |
   |                       |                       | Maximum length: 64 characters                      |
   +-----------------------+-----------------------+----------------------------------------------------+
   | log_group_id          | String                | Log group ID.                                      |
   |                       |                       |                                                    |
   |                       |                       | Value length: 36 characters                        |
   +-----------------------+-----------------------+----------------------------------------------------+
   | ttl_in_days           | Integer               | Log retention duration, in days (fixed to 7 days). |
   +-----------------------+-----------------------+----------------------------------------------------+

**Status code: 400**

.. table:: **Table 5** Response body parameters

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

**Status code: 401**

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

**Status code: 403**

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

**Status code: 500**

.. table:: **Table 8** Response body parameters

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

   POST https://{endpoint}/v2/{project_id}/groups/{log_group_id}

   /v2/{project_id}/groups/{log_group_id}
   {
     "ttl_in_days": 8
   }

Example Response
----------------

**Status code: 200**

.. code-block::

   {"creation_time" : "number","log_group_name" : "string","log_group_id" : "string","ttl_in_days" : 8}

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
     "error_code" : "LTS.0414",
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
     "error_msg" : "Failed to update log group"
   }

Status Codes
------------

+-------------+--------------------------------------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                                                    |
+=============+================================================================================================================================+
| 200         | The request has succeeded and the log group has been modified.                                                                 |
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
