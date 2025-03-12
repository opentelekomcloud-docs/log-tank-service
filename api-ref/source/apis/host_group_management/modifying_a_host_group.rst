:original_name: UpdateHostGroup.html

.. _UpdateHostGroup:

Modifying a Host Group
======================

Function
--------

Modify a host group.

URI
---

PUT /v3/{project_id}/lts/host-group

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                |
   +=================+=================+=================+============================================================================================================================================================+
   | project_id      | Yes             | String          | Project ID. For details about how to obtain a project ID, see :ref:`Obtaining the Project ID, Account ID, Log Group ID, and Log Stream ID <lts_api_0006>`. |
   |                 |                 |                 |                                                                                                                                                            |
   |                 |                 |                 | Minimum: **1**                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                            |
   |                 |                 |                 | Maximum: **64**                                                                                                                                            |
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

   +-----------------+-----------------+------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                         | Description                                                                                                                                              |
   +=================+=================+==============================================================================+==========================================================================================================================================================+
   | host_group_id   | Yes             | String                                                                       | Host group ID.                                                                                                                                           |
   |                 |                 |                                                                              |                                                                                                                                                          |
   |                 |                 |                                                                              | Minimum: **36**                                                                                                                                          |
   |                 |                 |                                                                              |                                                                                                                                                          |
   |                 |                 |                                                                              | Maximum: **36**                                                                                                                                          |
   +-----------------+-----------------+------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | host_group_name | No              | String                                                                       | Host group name. Use only letters, digits, underscores (_), hyphens (-), and periods (.). Do not start with a period or underscore or end with a period. |
   |                 |                 |                                                                              |                                                                                                                                                          |
   |                 |                 |                                                                              | Minimum: **1**                                                                                                                                           |
   |                 |                 |                                                                              |                                                                                                                                                          |
   |                 |                 |                                                                              | Maximum: **64**                                                                                                                                          |
   +-----------------+-----------------+------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | host_id_list    | No              | Array of strings                                                             | Host ID list. The host type must be the same as the host group type.                                                                                     |
   |                 |                 |                                                                              |                                                                                                                                                          |
   |                 |                 |                                                                              | Minimum: **36**                                                                                                                                          |
   |                 |                 |                                                                              |                                                                                                                                                          |
   |                 |                 |                                                                              | Maximum: **36**                                                                                                                                          |
   +-----------------+-----------------+------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | host_group_tag  | No              | Array of :ref:`HostGroupTag <updatehostgroup__request_hostgrouptag>` objects | Host group tags. A key must be unique. Up to 20 keys are allowed.                                                                                        |
   +-----------------+-----------------+------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | labels          | Yes             | Array of strings                                                             | Host group identifier. This parameter is mandatory when the host group type is **LABEL**.                                                                |
   +-----------------+-----------------+------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _updatehostgroup__request_hostgrouptag:

.. table:: **Table 4** HostGroupTag

   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                                                |
   +===========+===========+========+============================================================================================================================================================+
   | key       | Yes       | String | Tag key. Use only UTF-8 letters, digits, spaces, and the following characters: .:=+-@. Do not start with an underscore (). Max 128 characters are allowed. |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value     | No        | String | Tag value. Use only UTF-8 letters, digits, spaces, and the following characters: ``_.:/=+-@.`` Max 255 characters are allowed.                             |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   +-----------------+-------------------------------------------------------------------------------+------------------+
   | Parameter       | Type                                                                          | Description      |
   +=================+===============================================================================+==================+
   | host_group_id   | String                                                                        | Host group ID.   |
   +-----------------+-------------------------------------------------------------------------------+------------------+
   | host_group_name | String                                                                        | Host group name. |
   +-----------------+-------------------------------------------------------------------------------+------------------+
   | host_group_type | String                                                                        | Host group type. |
   +-----------------+-------------------------------------------------------------------------------+------------------+
   | host_id_list    | Array of strings                                                              | Host ID list.    |
   +-----------------+-------------------------------------------------------------------------------+------------------+
   | host_group_tag  | Array of :ref:`HostGroupTag <updatehostgroup__response_hostgrouptag>` objects | Tag information. |
   +-----------------+-------------------------------------------------------------------------------+------------------+
   | create_time     | Long                                                                          | Creation time.   |
   +-----------------+-------------------------------------------------------------------------------+------------------+
   | update_time     | Long                                                                          | Update time.     |
   +-----------------+-------------------------------------------------------------------------------+------------------+

.. _updatehostgroup__response_hostgrouptag:

.. table:: **Table 6** HostGroupTag

   ========= ====== ===========
   Parameter Type   Description
   ========= ====== ===========
   key       String Tag key.
   value     String Tag value.
   ========= ====== ===========

**Status code: 400**

.. table:: **Table 7** Response body parameters

   ========== ====== =================
   Parameter  Type   Description
   ========== ====== =================
   error_code String Error code
   error_msg  String Error description
   ========== ====== =================

**Status code: 500**

.. table:: **Table 8** Response body parameters

   ========== ====== =================
   Parameter  Type   Description
   ========== ====== =================
   error_code String Error code
   error_msg  String Error description
   ========== ====== =================

Example Requests
----------------

Update a host group. Parameter host_group_id is mandatory.

.. code-block:: text

   PUT https://{endpoint}/v3/{project_id}/lts/host-group

   {
     "host_group_id" : "xxxxxx",
     "host_group_name" : "qweqwe",
     "host_id_list" : [ "host_id_1", "host_id_2" ],
     "host_group_tag" : [ {
       "key" : "xxx",
       "value" : "xxx"
     } ]
   }

Example Responses
-----------------

**Status code: 200**

The host group is modified.

.. code-block::

   {
     "host_group_id" : "xxxxxx",
     "host_group_name" : "qweqwe",
     "host_group_type" : "linux",
     "host_id_list" : [ "host_id_1", "host_id_2" ],
     "host_group_tag" : [ {
       "key" : "xxx",
       "value" : "xxx"
     } ],
     "create_time" : 16351494332,
     "update_time" : 16351494332
   }

**Status code: 400**

Invalid request. Modify the request based on the description in **error_msg** before a retry.

.. code-block::

   {
     "error_code" : "LTS.1807",
     "error_msg" : "Invalid host group id"
   }

**Status code: 500**

The server has received the request but encountered an internal error.

.. code-block::

   {
     "error_code" : "LTS.0010",
     "error_msg" : "Internal Server Error"
   }

Status Codes
------------

+-------------+-----------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                   |
+=============+===============================================================================================+
| 200         | The host group is modified.                                                                   |
+-------------+-----------------------------------------------------------------------------------------------+
| 400         | Invalid request. Modify the request based on the description in **error_msg** before a retry. |
+-------------+-----------------------------------------------------------------------------------------------+
| 500         | The server has received the request but encountered an internal error.                        |
+-------------+-----------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
