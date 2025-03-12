:original_name: DeleteHostGroup.html

.. _DeleteHostGroup:

Deleting a Host Group
=====================

Function
--------

Delete a host group.

URI
---

DELETE /v3/{project_id}/lts/host-group

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

   +--------------------+-----------------+------------------+-------------------------+
   | Parameter          | Mandatory       | Type             | Description             |
   +====================+=================+==================+=========================+
   | host_group_id_list | Yes             | Array of strings | List of host group IDs. |
   |                    |                 |                  |                         |
   |                    |                 |                  | Minimum: **36**         |
   |                    |                 |                  |                         |
   |                    |                 |                  | Maximum: **36**         |
   +--------------------+-----------------+------------------+-------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------------------+---------------------------------------------------------------------------------------+--------------------------------+
   | Parameter             | Type                                                                                  | Description                    |
   +=======================+=======================================================================================+================================+
   | result                | Array of :ref:`GetHostGroupInfo <deletehostgroup__response_gethostgroupinfo>` objects | Host group details.            |
   +-----------------------+---------------------------------------------------------------------------------------+--------------------------------+
   | total                 | Long                                                                                  | Number of deleted host groups. |
   |                       |                                                                                       |                                |
   |                       |                                                                                       | Minimum: **0**                 |
   |                       |                                                                                       |                                |
   |                       |                                                                                       | Maximum: **1000**              |
   +-----------------------+---------------------------------------------------------------------------------------+--------------------------------+

.. _deletehostgroup__response_gethostgroupinfo:

.. table:: **Table 5** GetHostGroupInfo

   +-------------------+---------------------------------------------------------------------------------------------+-------------------+
   | Parameter         | Type                                                                                        | Description       |
   +===================+=============================================================================================+===================+
   | host_group_id     | String                                                                                      | Host group ID.    |
   +-------------------+---------------------------------------------------------------------------------------------+-------------------+
   | host_group_name   | String                                                                                      | Host group name.  |
   +-------------------+---------------------------------------------------------------------------------------------+-------------------+
   | host_group_type   | String                                                                                      | Host group type.  |
   +-------------------+---------------------------------------------------------------------------------------------+-------------------+
   | host_id_list      | Array of strings                                                                            | Host ID list.     |
   +-------------------+---------------------------------------------------------------------------------------------+-------------------+
   | host_group_tag    | Array of :ref:`HostGroupTagResBody <deletehostgroup__response_hostgrouptagresbody>` objects | Tag information.  |
   +-------------------+---------------------------------------------------------------------------------------------+-------------------+
   | create_time       | Long                                                                                        | Creation time.    |
   +-------------------+---------------------------------------------------------------------------------------------+-------------------+
   | update_time       | Long                                                                                        | Update time.      |
   +-------------------+---------------------------------------------------------------------------------------------+-------------------+
   | labels            | Array of strings                                                                            | Host group ID.    |
   +-------------------+---------------------------------------------------------------------------------------------+-------------------+
   | agent_access_type | String                                                                                      | Host access type. |
   +-------------------+---------------------------------------------------------------------------------------------+-------------------+

.. _deletehostgroup__response_hostgrouptagresbody:

.. table:: **Table 6** HostGroupTagResBody

   +------------------------+---------+------------------------------------------------------------------------------------------------------------------+
   | Parameter              | Type    | Description                                                                                                      |
   +========================+=========+==================================================================================================================+
   | key                    | String  | Tag key.                                                                                                         |
   +------------------------+---------+------------------------------------------------------------------------------------------------------------------+
   | value                  | String  | Tag value.                                                                                                       |
   +------------------------+---------+------------------------------------------------------------------------------------------------------------------+
   | tags_to_streams_enable | Boolean | Whether to apply the tag to the log stream. Only a tag of a log group can be directly applied to its log stream. |
   +------------------------+---------+------------------------------------------------------------------------------------------------------------------+

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

Delete one or multiple host groups at a time.

.. code-block:: text

   DELETE https://{endpoint}/v3/{project_id}/lts/host-group

   /v3/{project_id}/lts/host-group
   {"host_group_id_list":["xxxx","xxxx"]}

Example Responses
-----------------

**Status code: 200**

Host groups are deleted.

.. code-block::

   {
       "result" : [{
               "host_group_id" : "598c77aa-c69b-42f0-8cb8-xxxx5b38",
               "host_group_name" : "devspoxxxou1",
               "host_group_type" : "linux",
               "host_id_list" : ["dc1dab7e-b04xxxx", "xxxxx"],
               "host_group_tag" : [{
                       "key" : "xxx",
                       "value" : "xxx"
                   }, {
                       "key" : "xxx",
                       "value" : "xxx"
                   }
               ],
               "create_time" : 1635xx9410332,
               "update_time" : 163xx0332
           }
       ],
       "total" : 1
   }

**Status code: 400**

Invalid request. Modify the request based on the description in **error_msg** before a retry.

.. code-block::

   {
     "error_code" : "LTS.1812",
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
| 200         | Host groups are deleted.                                                                      |
+-------------+-----------------------------------------------------------------------------------------------+
| 400         | Invalid request. Modify the request based on the description in **error_msg** before a retry. |
+-------------+-----------------------------------------------------------------------------------------------+
| 500         | The server has received the request but encountered an internal error.                        |
+-------------+-----------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
