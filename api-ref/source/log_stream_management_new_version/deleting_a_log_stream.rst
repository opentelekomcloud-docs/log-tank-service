:original_name: lts_api_0018.html

.. _lts_api_0018:

Deleting a Log Stream
=====================

Function
--------

This API is used to delete a specified log stream from a specified log group. If a log transfer task has been associated with the log stream, delete the task first.

URI
---

DELETE /v2/{project_id}/groups/{log_group_id}/streams/{log_stream_id}

.. table:: **Table 1** URI parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                            |
   +=================+=================+=================+========================================================================================================================================================================================+
   | project_id      | Yes             | String          | Project ID. For details about how to obtain the ID, see :ref:`Obtaining the AccountID, Project ID, Log Group ID, and Log Stream ID <lts_api_0006>`.                                    |
   |                 |                 |                 |                                                                                                                                                                                        |
   |                 |                 |                 | Default value: None                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                        |
   |                 |                 |                 | Value length: 32 characters                                                                                                                                                            |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_group_id    | Yes             | String          | ID of the log group whose log streams will be deleted.                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                        |
   |                 |                 |                 | Default value: None                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                        |
   |                 |                 |                 | Value length: 36 characters                                                                                                                                                            |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_stream_id   | Yes             | String          | ID of the log stream to be deleted. For details about how to obtain the log stream ID, see :ref:`Obtaining the AccountID, Project ID, Log Group ID, and Log Stream ID <lts_api_0006>`. |
   |                 |                 |                 |                                                                                                                                                                                        |
   |                 |                 |                 | Default value: None                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                        |
   |                 |                 |                 | Value length: 36 characters                                                                                                                                                            |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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
   |                 |                 |                 | Value length: 30 characters                               |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------+

Response Parameters
-------------------

**Status code: 400**

.. table:: **Table 3** Response body parameters

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

.. table:: **Table 4** Response body parameters

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

**Status code: 500**

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

**Status code: 503**

.. table:: **Table 7** Response body parameter

   ========= ====== =====================================
   Parameter Type   Description
   ========= ====== =====================================
   ``-``     String The requested service is unavailable.
   ========= ====== =====================================

Example Request
---------------

.. code-block:: text

   DELETE https://{endpoint}/v2/{project_id}/groups/{log_group_id}/streams/{log_stream_id}

   /v2/{project_id}/groups/{log_group_id}/streams/{log_stream_id}

Example Response
----------------

**Status code: 400**

The request is invalid. Modify the request based on the description in **error_msg** before a retry.

.. code-block::

   {
     "error_code" : "LTS.0208",
     "error_msg" : "The log stream does not existed"
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
     "error_code" : "LTS.0203",
     "error_msg" : "Failed to delete Log stream"
   }

Status Codes
------------

+-------------+--------------------------------------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                                                    |
+=============+================================================================================================================================+
| 204         | The request has succeeded and the log stream has been deleted.                                                                 |
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
