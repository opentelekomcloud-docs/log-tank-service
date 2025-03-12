:original_name: CreateTags.html

.. _CreateTags:

Tag Management
==============

Function
--------

This API is used to tag a resource.

URI
---

POST /v1/{project_id}/{resource_type}/{resource_id}/tags/action

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
   | resource_type   | Yes             | String          | Resource type. The value can be **groups** or **topics**.                                                                                                  |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | resource_id     | Yes             | String          | Resource ID.                                                                                                                                               |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                   |
   +=================+=================+=================+===============================================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token obtained from IAM. For details about how to obtain a user token, see :ref:`Obtaining a User Token <lts_api_0004>`. |
   |                 |                 |                 |                                                                                                                               |
   |                 |                 |                 | Minimum: **1**                                                                                                                |
   |                 |                 |                 |                                                                                                                               |
   |                 |                 |                 | Maximum: **10000**                                                                                                            |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type    | Yes             | String          | Set this parameter to application/json;charset=UTF-8.                                                                         |
   |                 |                 |                 |                                                                                                                               |
   |                 |                 |                 | Minimum: **30**                                                                                                               |
   |                 |                 |                 |                                                                                                                               |
   |                 |                 |                 | Maximum: **30**                                                                                                               |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------+-----------+-----------------------------------------------------------------+---------------------------------------------------------+
   | Parameter | Mandatory | Type                                                            | Description                                             |
   +===========+===========+=================================================================+=========================================================+
   | action    | Yes       | String                                                          | Method of adding tags.                                  |
   +-----------+-----------+-----------------------------------------------------------------+---------------------------------------------------------+
   | is_open   | Yes       | Boolean                                                         | Whether to call external APIs.                          |
   +-----------+-----------+-----------------------------------------------------------------+---------------------------------------------------------+
   | tags      | Yes       | Array of :ref:`tagsBody <createtags__request_tagsbody>` objects | Tag field information. Up to 20 tag fields are allowed. |
   +-----------+-----------+-----------------------------------------------------------------+---------------------------------------------------------+

.. _createtags__request_tagsbody:

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

**Status code: 200**

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 201**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 400**

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 8** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

-  Creating a Tag

   .. code-block:: text

      POST /v1/2a473356cca5487f8373be891bffc1cf/groups/0933a172-379e-44d0-9ed9-f491b1c528ea/tags/action

      {
        "action" : "create",
        "is_open" : true,
        "tags" : [ {
          "key" : "zzz",
          "value" : "zzz"
        }, {
          "key" : "sgq",
          "value" : "123"
        } ]
      }

-  Deleting a tag

   .. code-block:: text

      POST /v1/2a473356cca5487f8373be891bffc1cf/groups/0933a172-379e-44d0-9ed9-f491b1c528ea/tags/action

      {
        "action" : "delete",
        "is_open" : true,
        "tags" : [ {
          "key" : "zzz",
          "value" : "zzz"
        }, {
          "key" : "sgq",
          "value" : "123"
        } ]
      }

Example Responses
-----------------

**Status code: 200**

Succeeded.

.. code-block::

   none

**Status code: 201**

Succeeded.

.. code-block::

   none

**Status code: 400**

Invalid request. Modify the request based on the description in **error_msg** before a retry.

.. code-block::

   {
     "error_code" : "LTS.1836",
     "error_msg" : "action is create or delete"
   }

**Status code: 500**

The server has received the request but encountered an internal error.

.. code-block::

   {
     "error_code" : "LTS.0203",
     "error_msg" : "Internal Server Error"
   }

Status Codes
------------

+-------------+-----------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                   |
+=============+===============================================================================================+
| 200         | Succeeded.                                                                                    |
+-------------+-----------------------------------------------------------------------------------------------+
| 201         | Succeeded.                                                                                    |
+-------------+-----------------------------------------------------------------------------------------------+
| 400         | Invalid request. Modify the request based on the description in **error_msg** before a retry. |
+-------------+-----------------------------------------------------------------------------------------------+
| 500         | The server has received the request but encountered an internal error.                        |
+-------------+-----------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
