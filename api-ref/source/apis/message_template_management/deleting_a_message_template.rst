:original_name: DeleteNotificationTemplate.html

.. _DeleteNotificationTemplate:

Deleting a Message Template
===========================

Function
--------

This API is used to delete a notification template.

URI
---

DELETE /v2/{project_id}/{domain_id}/lts/events/notification/templates

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                 |
   +=================+=================+=================+=============================================================================================================================================================+
   | project_id      | Yes             | String          | Project ID. For details about how to obtain a project ID, see :ref:`Obtaining the Project ID, Account ID, Log Group ID, and Log Stream ID <lts_api_0006>`.  |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | Minimum: **32**                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | Maximum: **32**                                                                                                                                             |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | domain_id       | Yes             | String          | Account ID. For details about how to obtain an account ID, see :ref:`Obtaining the Project ID, Account ID, Log Group ID, and Log Stream ID <lts_api_0006>`. |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | Minimum: **32**                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | Maximum: **32**                                                                                                                                             |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   +----------------+-----------+------------------+--------------------------------------------+
   | Parameter      | Mandatory | Type             | Description                                |
   +================+===========+==================+============================================+
   | template_names | Yes       | Array of strings | Array of names of templates to be deleted. |
   +----------------+-----------+------------------+--------------------------------------------+

Response Parameters
-------------------

**Status code: 400**

.. table:: **Table 4** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Deleting a message template

.. code-block:: text

   DELETE https://{endpoint}/v2/{project_id}/{domain_id}/lts/events/notification/templates

   /v2/{project_id}/{domain_id}/lts/events/notification/templates
   {"template_names":["template1","template2"]}

Example Responses
-----------------

**Status code: 400**

Invalid request. Modify the request based on the description in **error_msg** before a retry.

.. code-block::

   {
     "error_code" : "LTS.2015",
     "error_msg" : "delete template name is empty or projectId is null"
   }

**Status code: 500**

The server has received the request but encountered an internal error.

.. code-block::

   {
     "error_code" : "LTS.2015",
     "error_msg" : "Failed to delete notification template."
   }

Status Codes
------------

+-------------+-----------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                   |
+=============+===============================================================================================+
| 204         | If the response body is empty, the request is successfully responded.                         |
+-------------+-----------------------------------------------------------------------------------------------+
| 400         | Invalid request. Modify the request based on the description in **error_msg** before a retry. |
+-------------+-----------------------------------------------------------------------------------------------+
| 500         | The server has received the request but encountered an internal error.                        |
+-------------+-----------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
