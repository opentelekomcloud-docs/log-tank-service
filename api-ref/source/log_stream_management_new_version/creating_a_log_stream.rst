:original_name: lts_api_0016.html

.. _lts_api_0016:

Creating a Log Stream
=====================

Function
--------

This API is used to create a log stream in a specified log group.

URI
---

POST /v2/{project_id}/groups/{log_group_id}/streams

.. table:: **Table 1** URI parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                             |
   +=================+=================+=================+=========================================================================================================================================================================+
   | project_id      | Yes             | String          | Project ID. For details about how to obtain the ID, see :ref:`Obtaining the AccountID, Project ID, Log Group ID, and Log Stream ID <lts_api_0006>`. Default value: None |
   |                 |                 |                 |                                                                                                                                                                         |
   |                 |                 |                 | Value length: 32 characters                                                                                                                                             |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_group_id    | Yes             | String          | ID of the log group to which the log stream to be created will belong.                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                         |
   |                 |                 |                 | Default value: None                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                         |
   |                 |                 |                 | Value length: 36 characters                                                                                                                                             |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   +-----------------+-----------------+-----------------+---------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                           |
   +=================+=================+=================+=======================================+
   | log_stream_name | Yes             | String          | Name of the log stream to be created. |
   |                 |                 |                 |                                       |
   |                 |                 |                 | Minimum length: 1 character           |
   |                 |                 |                 |                                       |
   |                 |                 |                 | Maximum length: 64 characters         |
   |                 |                 |                 |                                       |
   |                 |                 |                 | Enumerated value:                     |
   |                 |                 |                 |                                       |
   |                 |                 |                 | -  **lts-stream-13ci**                |
   +-----------------+-----------------+-----------------+---------------------------------------+

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 4** Response body parameter

   +-----------------------+-----------------------+-------------------------------+
   | Parameter             | Type                  | Description                   |
   +=======================+=======================+===============================+
   | log_stream_id         | String                | ID of the created log stream. |
   |                       |                       |                               |
   |                       |                       | Value length: 36 characters   |
   +-----------------------+-----------------------+-------------------------------+

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

.. table:: **Table 9** Response body parameter

   ========= ====== =====================================
   Parameter Type   Description
   ========= ====== =====================================
   ``-``     String The requested service is unavailable.
   ========= ====== =====================================

Example Request
---------------

.. code-block:: text

   POST https://{endpoint}/v2/{project_id}/groups/{log_group_id}/streams

   /v2/{project_id}/groups/{log_group_id}/streams
   {
     "log_stream_name": "lts-stream-02kh",
     "ttl_in_days": 7,

   }


Example Response
----------------

**Status code: 201**

.. code-block::

   {
     "log_stream_id":"c54dbc58-0fd8-48ed-b007-6d54981427a7"
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
     "error_code" : "LTS.0202",
     "error_msg" : "Failed to create Log stream"
   }

Status Codes
------------

+-------------+--------------------------------------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                                                    |
+=============+================================================================================================================================+
| 201         | The request has succeeded and the log stream has been created.                                                                 |
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
