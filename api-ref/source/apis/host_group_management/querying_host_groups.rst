:original_name: ListHostGroup.html

.. _ListHostGroup:

Querying Host Groups
====================

Function
--------

Query the host group list.

URI
---

POST /v3/{project_id}/lts/host-group-list

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

   +--------------------+-----------------+--------------------------------------------------------------------------------------+-------------------------+
   | Parameter          | Mandatory       | Type                                                                                 | Description             |
   +====================+=================+======================================================================================+=========================+
   | host_group_id_list | No              | Array of strings                                                                     | List of host group IDs. |
   |                    |                 |                                                                                      |                         |
   |                    |                 |                                                                                      | Minimum: **36**         |
   |                    |                 |                                                                                      |                         |
   |                    |                 |                                                                                      | Maximum: **36**         |
   +--------------------+-----------------+--------------------------------------------------------------------------------------+-------------------------+
   | filter             | Yes             | :ref:`GetHostGroupListFilter <listhostgroup__request_gethostgrouplistfilter>` object | Host group filters.     |
   +--------------------+-----------------+--------------------------------------------------------------------------------------+-------------------------+

.. _listhostgroup__request_gethostgrouplistfilter:

.. table:: **Table 4** GetHostGroupListFilter

   +----------------------+-----------------+--------------------------------------------------------------------------------+---------------------------+
   | Parameter            | Mandatory       | Type                                                                           | Description               |
   +======================+=================+================================================================================+===========================+
   | host_group_type      | No              | String                                                                         | Host group type.          |
   |                      |                 |                                                                                |                           |
   |                      |                 |                                                                                | -  Windows                |
   |                      |                 |                                                                                | -  Linux                  |
   +----------------------+-----------------+--------------------------------------------------------------------------------+---------------------------+
   | host_group_name_list | No              | Array of strings                                                               | List of host group names. |
   |                      |                 |                                                                                |                           |
   |                      |                 |                                                                                | Minimum: **1**            |
   |                      |                 |                                                                                |                           |
   |                      |                 |                                                                                | Maximum: **64**           |
   +----------------------+-----------------+--------------------------------------------------------------------------------+---------------------------+
   | host_name_list       | No              | Array of strings                                                               | Host name list.           |
   |                      |                 |                                                                                |                           |
   |                      |                 |                                                                                | Minimum: **1**            |
   |                      |                 |                                                                                |                           |
   |                      |                 |                                                                                | Maximum: **128**          |
   +----------------------+-----------------+--------------------------------------------------------------------------------+---------------------------+
   | host_group_tag       | No              | :ref:`GetHostGroupListTag <listhostgroup__request_gethostgrouplisttag>` object | Host group tags.          |
   +----------------------+-----------------+--------------------------------------------------------------------------------+---------------------------+

.. _listhostgroup__request_gethostgrouplisttag:

.. table:: **Table 5** GetHostGroupListTag

   +-----------+-----------+----------------------------------------------------------------------------+---------------------------------------------------+
   | Parameter | Mandatory | Type                                                                       | Description                                       |
   +===========+===========+============================================================================+===================================================+
   | tag_type  | No        | String                                                                     | Tag type. Tag filtering logic: **AND** or **OR**. |
   +-----------+-----------+----------------------------------------------------------------------------+---------------------------------------------------+
   | tag_list  | No        | Array of :ref:`HostGroupTag <listhostgroup__request_hostgrouptag>` objects | Host group tags.                                  |
   +-----------+-----------+----------------------------------------------------------------------------+---------------------------------------------------+

.. _listhostgroup__request_hostgrouptag:

.. table:: **Table 6** HostGroupTag

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

.. table:: **Table 7** Response body parameters

   +-----------+-------------------------------------------------------------------------------------+------------------------------+
   | Parameter | Type                                                                                | Description                  |
   +===========+=====================================================================================+==============================+
   | result    | Array of :ref:`GetHostGroupInfo <listhostgroup__response_gethostgroupinfo>` objects | Host group list.             |
   +-----------+-------------------------------------------------------------------------------------+------------------------------+
   | total     | Long                                                                                | Total number of host groups. |
   +-----------+-------------------------------------------------------------------------------------+------------------------------+

.. _listhostgroup__response_gethostgroupinfo:

.. table:: **Table 8** GetHostGroupInfo

   +-------------------+-------------------------------------------------------------------------------------------+-------------------+
   | Parameter         | Type                                                                                      | Description       |
   +===================+===========================================================================================+===================+
   | host_group_id     | String                                                                                    | Host group ID.    |
   +-------------------+-------------------------------------------------------------------------------------------+-------------------+
   | host_group_name   | String                                                                                    | Host group name.  |
   +-------------------+-------------------------------------------------------------------------------------------+-------------------+
   | host_group_type   | String                                                                                    | Host group type.  |
   +-------------------+-------------------------------------------------------------------------------------------+-------------------+
   | host_id_list      | Array of strings                                                                          | Host ID list.     |
   +-------------------+-------------------------------------------------------------------------------------------+-------------------+
   | host_group_tag    | Array of :ref:`HostGroupTagResBody <listhostgroup__response_hostgrouptagresbody>` objects | Tag information.  |
   +-------------------+-------------------------------------------------------------------------------------------+-------------------+
   | create_time       | Long                                                                                      | Creation time.    |
   +-------------------+-------------------------------------------------------------------------------------------+-------------------+
   | update_time       | Long                                                                                      | Update time.      |
   +-------------------+-------------------------------------------------------------------------------------------+-------------------+
   | labels            | Array of strings                                                                          | Host group ID.    |
   +-------------------+-------------------------------------------------------------------------------------------+-------------------+
   | agent_access_type | String                                                                                    | Host access type. |
   +-------------------+-------------------------------------------------------------------------------------------+-------------------+

.. _listhostgroup__response_hostgrouptagresbody:

.. table:: **Table 9** HostGroupTagResBody

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

.. table:: **Table 10** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 11** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Host groups are sorted by filters specified in the request body. If no filters are configured in the body, all host groups are queried.

.. code-block:: text

   POST https://{endpoint}/v3/{project_id}/lts/host-group-list

   {
     "host_group_id_list" : [ "bca6d903-3528-42a8-91f4-586722cxxxxx" ],
     "filter" : {
       "host_group_type" : "linux",
       "host_group_name_list" : [ "wjyTxxx" ],
       "host_name_list" : [ "ecs-apmtexxxdeletion" ],
       "host_group_tag" : {
         "tag_type" : "AND",
         "tag_list" : [ {
           "key" : "xxx",
           "value" : "xxx",
           "tags_to_streams_enable" : true
         } ]
       }
     }
   }

Example Responses
-----------------

**Status code: 200**

The host group query is successful.

.. code-block::

   {
     "result" : [ {
       "host_group_id" : "598c77aa-c69b-42f0-8cb8-xxxx5b38",
       "host_group_name" : "wjyTxxx",
       "host_group_type" : "linux",
       "host_id_list" : [ "dc1dab7e-b04xxxx", "xxxxx" ],
       "host_group_tag" : [ {
         "key" : "xxx",
         "value" : "xxx"
       } ],
       "create_time" : 1635459410332,
       "update_time" : 163560332
     } ],
     "total" : 1
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
| 200         | The host group query is successful.                                                           |
+-------------+-----------------------------------------------------------------------------------------------+
| 400         | Invalid request. Modify the request based on the description in **error_msg** before a retry. |
+-------------+-----------------------------------------------------------------------------------------------+
| 500         | The server has received the request but encountered an internal error.                        |
+-------------+-----------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
