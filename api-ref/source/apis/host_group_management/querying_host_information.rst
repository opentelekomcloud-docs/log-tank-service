:original_name: ListHost.html

.. _ListHost:

Querying Host Information
=========================

Function
--------

Query the host list.

URI
---

POST /v3/{project_id}/lts/host-list

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
   | Content-Type    | Yes             | String          | Set this parameter to **application/json;charset=utf8**.                                                                      |
   |                 |                 |                 |                                                                                                                               |
   |                 |                 |                 | Minimum: **30**                                                                                                               |
   |                 |                 |                 |                                                                                                                               |
   |                 |                 |                 | Maximum: **30**                                                                                                               |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+-----------------------------------------------------------------------+------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                  | Description                                    |
   +=================+=================+=======================================================================+================================================+
   | host_id_list    | No              | Array of strings                                                      | Host ID list. You can filter hosts by host ID. |
   |                 |                 |                                                                       |                                                |
   |                 |                 |                                                                       | Minimum: **36**                                |
   |                 |                 |                                                                       |                                                |
   |                 |                 |                                                                       | Maximum: **36**                                |
   +-----------------+-----------------+-----------------------------------------------------------------------+------------------------------------------------+
   | filter          | Yes             | :ref:`GetHostListFilter <listhost__request_gethostlistfilter>` object | Filters other than host IDs.                   |
   +-----------------+-----------------+-----------------------------------------------------------------------+------------------------------------------------+

.. _listhost__request_gethostlistfilter:

.. table:: **Table 4** GetHostListFilter

   +-----------------+-----------------+------------------+---------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                         |
   +=================+=================+==================+=====================================================================+
   | host_name_list  | No              | Array of strings | Host name list. You can filter hosts by host name.                  |
   |                 |                 |                  |                                                                     |
   |                 |                 |                  | Minimum: **1**                                                      |
   |                 |                 |                  |                                                                     |
   |                 |                 |                  | Maximum: **128**                                                    |
   +-----------------+-----------------+------------------+---------------------------------------------------------------------+
   | host_ip_list    | No              | Array of strings | List of host IP addresses. You can filter hosts by host IP address. |
   |                 |                 |                  |                                                                     |
   |                 |                 |                  | Minimum: **1**                                                      |
   |                 |                 |                  |                                                                     |
   |                 |                 |                  | Maximum: **16**                                                     |
   +-----------------+-----------------+------------------+---------------------------------------------------------------------+
   | host_status     | No              | String           | Host status. You can filter hosts by host status.                   |
   |                 |                 |                  |                                                                     |
   |                 |                 |                  | -  **uninstall**: not installed.                                    |
   |                 |                 |                  |                                                                     |
   |                 |                 |                  | -  **running**: running.                                            |
   |                 |                 |                  |                                                                     |
   |                 |                 |                  | -  **offline**: offline.                                            |
   |                 |                 |                  |                                                                     |
   |                 |                 |                  | -  **error**: abnormal.                                             |
   |                 |                 |                  |                                                                     |
   |                 |                 |                  | -  **plugin error**: plug-in error.                                 |
   |                 |                 |                  |                                                                     |
   |                 |                 |                  | -  **installing**: installing.                                      |
   |                 |                 |                  |                                                                     |
   |                 |                 |                  | -  **install-fail**: Installation failed.                           |
   |                 |                 |                  |                                                                     |
   |                 |                 |                  | -  **upgrading**: upgrading.                                        |
   |                 |                 |                  |                                                                     |
   |                 |                 |                  | -  **upgrade failed**: Upgrade failed.                              |
   |                 |                 |                  |                                                                     |
   |                 |                 |                  | -  **uninstalling**: being uninstalled.                             |
   |                 |                 |                  |                                                                     |
   |                 |                 |                  | -  **authentication error**: Authentication failed.                 |
   +-----------------+-----------------+------------------+---------------------------------------------------------------------+
   | host_version    | No              | String           | Host version. You can filter hosts by host version.                 |
   |                 |                 |                  |                                                                     |
   |                 |                 |                  | Minimum: **1**                                                      |
   |                 |                 |                  |                                                                     |
   |                 |                 |                  | Maximum: **16**                                                     |
   +-----------------+-----------------+------------------+---------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   +-----------+------------------------------------------------------------------------------+------------------------+
   | Parameter | Type                                                                         | Description            |
   +===========+==============================================================================+========================+
   | result    | Array of :ref:`GetHostListInfo <listhost__response_gethostlistinfo>` objects | Host list.             |
   +-----------+------------------------------------------------------------------------------+------------------------+
   | total     | Long                                                                         | Total number of hosts. |
   +-----------+------------------------------------------------------------------------------+------------------------+

.. _listhost__response_gethostlistinfo:

.. table:: **Table 6** GetHostListInfo

   +-----------------------+-----------------------+-----------------------------------------------------+
   | Parameter             | Type                  | Description                                         |
   +=======================+=======================+=====================================================+
   | host_id               | String                | Host ID.                                            |
   +-----------------------+-----------------------+-----------------------------------------------------+
   | host_ip               | String                | Host IP.                                            |
   +-----------------------+-----------------------+-----------------------------------------------------+
   | host_name             | String                | Host name.                                          |
   +-----------------------+-----------------------+-----------------------------------------------------+
   | host_status           | String                | Host status.                                        |
   |                       |                       |                                                     |
   |                       |                       | -  **uninstall**: not installed.                    |
   |                       |                       |                                                     |
   |                       |                       | -  **running**: running.                            |
   |                       |                       |                                                     |
   |                       |                       | -  **offline**: offline.                            |
   |                       |                       |                                                     |
   |                       |                       | -  **error**: abnormal.                             |
   |                       |                       |                                                     |
   |                       |                       | -  **plugin error**: plug-in error.                 |
   |                       |                       |                                                     |
   |                       |                       | -  **installing**: installing.                      |
   |                       |                       |                                                     |
   |                       |                       | -  **install-fail**: Installation failed.           |
   |                       |                       |                                                     |
   |                       |                       | -  **upgrading**: upgrading.                        |
   |                       |                       |                                                     |
   |                       |                       | -  **upgrade failed**: Upgrade failed.              |
   |                       |                       |                                                     |
   |                       |                       | -  **uninstalling**: being uninstalled.             |
   |                       |                       |                                                     |
   |                       |                       | -  **authentication error**: Authentication failed. |
   +-----------------------+-----------------------+-----------------------------------------------------+
   | host_type             | String                | Host type.                                          |
   |                       |                       |                                                     |
   |                       |                       | -  Windows                                          |
   |                       |                       |                                                     |
   |                       |                       | -  Linux                                            |
   +-----------------------+-----------------------+-----------------------------------------------------+
   | host_version          | String                | Host version.                                       |
   +-----------------------+-----------------------+-----------------------------------------------------+
   | update_time           | Long                  | Update time.                                        |
   +-----------------------+-----------------------+-----------------------------------------------------+

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

Hosts are sorted by filters specified in the request body. If no filters are configured in the body, all host groups are queried.

.. code-block:: text

   POST https://{endpoint}/v3/{project_id}/lts/host-list

   {
     "host_id_list" : [ "713a9f81-574b-45aa-92df-24c4caxxxxxx", "c7085aa9-2142-4ada-9f78-bf81ffxxxxxx" ],
     "filter" : {
       "host_name_list" : [ "ecs-xxxx", "10.66.16xxx" ],
       "host_ip_list" : [ "192.168xxxx" ],
       "host_status" : "running",
       "host_version" : "5.13.xxxx"
     }
   }

Example Responses
-----------------

**Status code: 200**

The host query is successful.

.. code-block::

   {
     "result" : [ {
       "host_id" : "dc1dab7e-b045-4e77-bda4-914xxxxxx",
       "host_ip" : "172.16.xxxx",
       "host_name" : "ecs-apmtexxxxxx",
       "host_status" : "running",
       "host_type" : "linux",
       "host_version" : "5.13.xx.x",
       "update_time" : 1637223314526
     } ],
     "total" : 1
   }

**Status code: 400**

Invalid request. Modify the request based on the description in **error_msg** before a retry.

.. code-block::

   {
     "error_code" : "LTS.1807",
     "error_msg" : "Invalid host id"
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
| 200         | The host query is successful.                                                                 |
+-------------+-----------------------------------------------------------------------------------------------+
| 400         | Invalid request. Modify the request based on the description in **error_msg** before a retry. |
+-------------+-----------------------------------------------------------------------------------------------+
| 500         | The server has received the request but encountered an internal error.                        |
+-------------+-----------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
