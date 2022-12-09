:original_name: lts_api_0028.html

.. _lts_api_0028:

Querying Logs
=============

Function
--------

This API is used to query logs in a specified log stream.

URI
---

POST /v2/{project_id}/groups/{log_group_id}/streams/{log_stream_id}/content/query

.. table:: **Table 1** URI parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                         |
   +=================+=================+=================+=====================================================================================================================================================+
   | project_id      | Yes             | String          | Project ID. For details about how to obtain the ID, see :ref:`Obtaining the AccountID, Project ID, Log Group ID, and Log Stream ID <lts_api_0006>`. |
   |                 |                 |                 |                                                                                                                                                     |
   |                 |                 |                 | Default value: None                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                     |
   |                 |                 |                 | Value length: 32 characters                                                                                                                         |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_group_id    | Yes             | String          | Log group ID.                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                     |
   |                 |                 |                 | Default value: None                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                     |
   |                 |                 |                 | Value length: 36 characters                                                                                                                         |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_stream_id   | Yes             | String          | Log stream ID.                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                     |
   |                 |                 |                 | Default value: None                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                     |
   |                 |                 |                 | Value length: 36 characters                                                                                                                         |
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
   |                 |                 |                 | Minimum length: 30 characters                             |
   |                 |                 |                 |                                                           |
   |                 |                 |                 | Maximum length: 30 characters                             |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type               | Description                                                                                                                                                                                                                                                                                      |
   +=================+=================+====================+==================================================================================================================================================================================================================================================================================================+
   | start_time      | Yes             | String             | UTC start time of the search window (in milliseconds).                                                                                                                                                                                                                                           |
   |                 |                 |                    |                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                    | .. note::                                                                                                                                                                                                                                                                                        |
   |                 |                 |                    |                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                    |    Maximum query time range: 30 days                                                                                                                                                                                                                                                             |
   +-----------------+-----------------+--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | end_time        | Yes             | String             | UTC end time of the search window (in milliseconds).                                                                                                                                                                                                                                             |
   |                 |                 |                    |                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                    | .. note::                                                                                                                                                                                                                                                                                        |
   |                 |                 |                    |                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                    |    Maximum query time range: 30 days                                                                                                                                                                                                                                                             |
   +-----------------+-----------------+--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | labels          | No              | Map<String,String> | Filter criteria, which vary between log sources.                                                                                                                                                                                                                                                 |
   +-----------------+-----------------+--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | keywords        | No              | String             | Keyword used for search. A keyword is a word between two adjacent delimiters.                                                                                                                                                                                                                    |
   |                 |                 |                    |                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                    | Enumerated value:                                                                                                                                                                                                                                                                                |
   |                 |                 |                    |                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                    | -  **error**                                                                                                                                                                                                                                                                                     |
   +-----------------+-----------------+--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | line_num        | No              | String             | Sequence number of a log event. This parameter is not required for the first query, but is required for subsequent pagination queries. The value can be obtained from the response of the last query. The value of **line_num** should be between the values of **start_time** and **end_time**. |
   |                 |                 |                    |                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                    | Value length: 19 characters                                                                                                                                                                                                                                                                      |
   +-----------------+-----------------+--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | is_desc         | No              | Boolean            | Whether the search order is descending or ascending. The default value is **false**, indicating that search results are displayed in ascending order.                                                                                                                                            |
   |                 |                 |                    |                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                    | Enumerated value:                                                                                                                                                                                                                                                                                |
   |                 |                 |                    |                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                    | -  **false**                                                                                                                                                                                                                                                                                     |
   +-----------------+-----------------+--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | search_type     | No              | String             | The value is **init** (default value) for the first query, or **forwards** or **backwards** for a pagination query. This parameter is used together with **is_desc** for pagination queries.                                                                                                     |
   |                 |                 |                    |                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                    | Enumerated value:                                                                                                                                                                                                                                                                                |
   |                 |                 |                    |                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                    | -  **forwards**                                                                                                                                                                                                                                                                                  |
   +-----------------+-----------------+--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer            | Number of logs to be queried each time. The value is **50** when this parameter is not set. You are advised to set this parameter to **100**.                                                                                                                                                    |
   |                 |                 |                    |                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                    | Minimum value: **1**                                                                                                                                                                                                                                                                             |
   |                 |                 |                    |                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                    | Maximum value: **5000**                                                                                                                                                                                                                                                                          |
   +-----------------+-----------------+--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameter

   +-----------+-------------------------------------------------------------------------------------------------+----------------------+
   | Parameter | Type                                                                                            | Description          |
   +===========+=================================================================================================+======================+
   | logs      | Array of :ref:`LogContents <lts_api_0028__en-us_topic_0266335031_response_logcontents>` objects | Information of logs. |
   +-----------+-------------------------------------------------------------------------------------------------+----------------------+
   | count     | Integer                                                                                         | Number of logs.      |
   +-----------+-------------------------------------------------------------------------------------------------+----------------------+

.. _lts_api_0028__en-us_topic_0266335031_response_logcontents:

.. table:: **Table 5** LogContents

   +-----------------------+-----------------------+---------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                               |
   +=======================+=======================+===========================================================================+
   | content               | String                | Raw log data.                                                             |
   |                       |                       |                                                                           |
   |                       |                       | Minimum length: 1 character                                               |
   |                       |                       |                                                                           |
   |                       |                       | Maximum length: 10,000 characters                                         |
   +-----------------------+-----------------------+---------------------------------------------------------------------------+
   | line_num              | String                | Sequence number of a log event.                                           |
   |                       |                       |                                                                           |
   |                       |                       | Value length: 19 characters                                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------+
   | labels                | Map<String,String>    | Labels contained in a log event. The labels vary depending on log events. |
   +-----------------------+-----------------------+---------------------------------------------------------------------------+

**Status code: 400**

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

**Status code: 401**

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

**Status code: 403**

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

**Status code: 500**

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

Log details:

.. code-block::

   2020-07-25/14:44:42 this log is Error NO 1
   2020-07-25/14:44:43 this log is Error NO 2
   2020-07-25/14:44:44 this log is Error NO 3
   2020-07-25/14:44:45 this log is Error NO 4
   2020-07-25/14:44:46 this log is Error NO 5
   2020-07-25/14:44:47 this log is Error NO 6
   2020-07-25/14:44:48 this log is Error NO 7
   2020-07-25/14:44:49 this log is Error NO 8
   2020-07-25/14:44:50 this log is Error NO 9
   2020-07-25/14:44:51 this log is Error NO 10

.. code-block:: text

   POST https://{endpoint}/v2/{project_id}/groups/{log_group_id}/streams/{log_stream_id}/content/query

-  For the first query:

   .. code-block::

      v2/{project_id}/groups/{log_group_id}/streams/{log_stream_id}/content/query
      {
        "start_time": 1595659200000,
        "end_time": 1595659500000,
        "labels":
            {
              "hostName": "ecs-kwxtest"
            },
        "keywords": "log",
        "limit": 10,
        "is_count":true
      }

-  For a pagination query (Assume that the search starts from the log event containing **NO 5** and the log events containing **NO 6**, **NO 7**, and **NO 8** are the target log events):

   .. code-block::

      v2/{project_id}/groups/{log_group_id}/streams/{log_stream_id}/content/query
      {
        "start_time": 1595659200000,
        "end_time": 1595659500000,
        "labels":
            {
              "hostName": "ecs-kwxtest"
            },
        "keywords": "log",
        "line_num": "1595659490239433658",
        "is_desc": "false",
        "search_type": "forwards",
        "limit": "3",
        "is_count":true
      }

-  For a pagination query (Assume that the search starts from the log event containing **NO 5** and the log events containing **NO 8**, **NO 7**, and **NO 6** are the target log events):

   .. code-block::

      {
        "start_time": 1595659200000,
        "end_time": 1595659500000,
        "labels":
            {
              "hostName": "ecs-kwxtest"
            },
        "keywords": "log",
        "line_num": "1595659490239433658",
        "is_desc": "true",
        "search_type": "backwards",
        "limit": "3",
        "is_count":true
      }

-  For a pagination query (Assume that the search starts from the log event containing **NO 5** and the log events containing **NO 2**, **NO 3**, and **NO 4** are the target log events):

   .. code-block::

      v2/{project_id}/groups/{log_group_id}/streams/{log_stream_id}/content/query
      {
        "start_time": 1595659200000,
        "end_time": 1595659500000,
        "labels":
            {
              "hostName": "ecs-kwxtest"
            },
        "keywords": "log",
        "line_num": "1595659490239433658",
        "is_desc": "false",
        "search_type": "backwards",
        "limit": "3",
        "is_count":true
      }

-  For a pagination query (Assume that the search starts from the log event containing **NO 5** and the log events containing **NO 4**, **NO 3**, and **NO 2** are the target log events):

   .. code-block::

      v2/{project_id}/groups/{log_group_id}/streams/{log_stream_id}/content/query
      {
        "start_time": 1595659200000,
        "end_time": 1595659500000,
        "labels":
            {
              "hostName": "ecs-kwxtest"
            },
        "keywords": "log",
        "line_num": "1595659490239433658",
        "is_desc": "true",
        "search_type": "forwards",
        "limit": "3",
        "is_count":true
      }

Example Response
----------------

-  For the first query:

   .. code-block::

      {
        "count": 32,
        "logs": [
              {
                  "content": "2020-07-25/14:44:42 this <HighLightTag>log</HighLightTag> is Error NO 1\n",
                  "labels": {
                      "hostName": "ecs-kwxtest",
                      "hostIP": "192.168.0.156",
                      "appName": "default_appname",
                      "containerName": "CONFIG_FILE",
                      "clusterName": "CONFIG_FILE",
                      "hostId": "9787ef31-fd7b-4eff-ba71-72d580f11f55",
                      "podName": "default_procname",
                      "clusterId": "CONFIG_FILE",
                      "nameSpace": "CONFIG_FILE",
                      "category": "LTS"
                  },
                  "line_num": "1595659490239433654"
              },
              {
                  "content": "2020-07-25/14:44:43 this <HighLightTag>log</HighLightTag> is Error NO 2\n",
                  "labels": {
                      "hostName": "ecs-kwxtest",
                      "hostIP": "192.168.0.156",
                      "appName": "default_appname",
                      "containerName": "CONFIG_FILE",
                      "clusterName": "CONFIG_FILE",
                      "hostId": "9787ef31-fd7b-4eff-ba71-72d580f11f55",
                      "podName": "default_procname",
                      "clusterId": "CONFIG_FILE",
                      "nameSpace": "CONFIG_FILE",
                      "category": "LTS"
                  },
                  "line_num": "1595659490239433655"
              },
              {
                  "content": "2020-07-25/14:44:44 this <HighLightTag>log</HighLightTag> is Error NO 3\n",
                  "labels": {
                      "hostName": "ecs-kwxtest",
                      "hostIP": "192.168.0.156",
                      "appName": "default_appname",
                      "containerName": "CONFIG_FILE",
                      "clusterName": "CONFIG_FILE",
                      "hostId": "9787ef31-fd7b-4eff-ba71-72d580f11f55",
                      "podName": "default_procname",
                      "clusterId": "CONFIG_FILE",
                      "nameSpace": "CONFIG_FILE",
                      "category": "LTS"
                  },
                  "line_num": "1595659490239433656"
              },
              {
                  "content": "2020-07-25/14:44:45 this <HighLightTag>log</HighLightTag> is Error NO 4\n",
                  "labels": {
                      "hostName": "ecs-kwxtest",
                      "hostIP": "192.168.0.156",
                      "appName": "default_appname",
                      "containerName": "CONFIG_FILE",
                      "clusterName": "CONFIG_FILE",
                      "hostId": "9787ef31-fd7b-4eff-ba71-72d580f11f55",
                      "podName": "default_procname",
                      "clusterId": "CONFIG_FILE",
                      "nameSpace": "CONFIG_FILE",
                      "category": "LTS"
                  },
                  "line_num": "1595659490239433657"
              },
              {
                  "content": "2020-07-25/14:44:46 this <HighLightTag>log</HighLightTag> is Error NO 5\n",
                  "labels": {
                      "hostName": "ecs-kwxtest",
                      "hostIP": "192.168.0.156",
                      "appName": "default_appname",
                      "containerName": "CONFIG_FILE",
                      "clusterName": "CONFIG_FILE",
                      "hostId": "9787ef31-fd7b-4eff-ba71-72d580f11f55",
                      "podName": "default_procname",
                      "clusterId": "CONFIG_FILE",
                      "nameSpace": "CONFIG_FILE",
                      "category": "LTS"
                  },
                  "line_num": "1595659490239433658"
              },
              {
                  "content": "2020-07-25/14:44:47 this <HighLightTag>log</HighLightTag> is Error NO 6\n",
                  "labels": {
                      "hostName": "ecs-kwxtest",
                      "hostIP": "192.168.0.156",
                      "appName": "default_appname",
                      "containerName": "CONFIG_FILE",
                      "clusterName": "CONFIG_FILE",
                      "hostId": "9787ef31-fd7b-4eff-ba71-72d580f11f55",
                      "podName": "default_procname",
                      "clusterId": "CONFIG_FILE",
                      "nameSpace": "CONFIG_FILE",
                      "category": "LTS"
                  },
                  "line_num": "1595659490239433659"
              },
              {
                  "content": "2020-07-25/14:44:48 this <HighLightTag>log</HighLightTag> is Error NO 7\n",
                  "labels": {
                      "hostName": "ecs-kwxtest",
                      "hostIP": "192.168.0.156",
                      "appName": "default_appname",
                      "containerName": "CONFIG_FILE",
                      "clusterName": "CONFIG_FILE",
                      "hostId": "9787ef31-fd7b-4eff-ba71-72d580f11f55",
                      "podName": "default_procname",
                      "clusterId": "CONFIG_FILE",
                      "nameSpace": "CONFIG_FILE",
                      "category": "LTS"
                  },
                  "line_num": "1595659490239433660"
              },
              {
                  "content": "2020-07-25/14:44:49 this <HighLightTag>log</HighLightTag> is Error NO 8\n",
                  "labels": {
                      "hostName": "ecs-kwxtest",
                      "hostIP": "192.168.0.156",
                      "appName": "default_appname",
                      "containerName": "CONFIG_FILE",
                      "clusterName": "CONFIG_FILE",
                      "hostId": "9787ef31-fd7b-4eff-ba71-72d580f11f55",
                      "podName": "default_procname",
                      "clusterId": "CONFIG_FILE",
                      "nameSpace": "CONFIG_FILE",
                      "category": "LTS"
                  },
                  "line_num": "1595659490239433661"
              },
              {
                  "content": "2020-07-25/14:44:50 this <HighLightTag>log</HighLightTag> is Error NO 9\n",
                  "labels": {
                      "hostName": "ecs-kwxtest",
                      "hostIP": "192.168.0.156",
                      "appName": "default_appname",
                      "containerName": "CONFIG_FILE",
                      "clusterName": "CONFIG_FILE",
                      "hostId": "9787ef31-fd7b-4eff-ba71-72d580f11f55",
                      "podName": "default_procname",
                      "clusterId": "CONFIG_FILE",
                      "nameSpace": "CONFIG_FILE",
                      "category": "LTS"
                  },
                  "line_num": "1595659490839420574"
              },
              {
                  "content": "2020-07-25/14:44:51 this <HighLightTag>log</HighLightTag> is Error NO 10\n",
                  "labels": {
                      "hostName": "ecs-kwxtest",
                      "hostIP": "192.168.0.156",
                      "appName": "default_appname",
                      "containerName": "CONFIG_FILE",
                      "clusterName": "CONFIG_FILE",
                      "hostId": "9787ef31-fd7b-4eff-ba71-72d580f11f55",
                      "podName": "default_procname",
                      "clusterId": "CONFIG_FILE",
                      "nameSpace": "CONFIG_FILE",
                      "category": "LTS"
                  },
                  "line_num": "1595659491839412667"
              }
      ]
      }

-  For a pagination query (Assume that the search starts from the log event containing **NO 5** and the log events containing **NO 6**, **NO 7**, and **NO 8** are the target log events):

   .. code-block::

      {
          "count": 32,
          "logs": [
              {
                  "content": "2020-07-25/14:44:47 this <HighLightTag>log</HighLightTag> is Error NO 6\n",
                  "labels": {
                      "hostName": "ecs-kwxtest",
                      "hostIP": "192.168.0.156",
                      "appName": "default_appname",
                      "containerName": "CONFIG_FILE",
                      "clusterName": "CONFIG_FILE",
                      "hostId": "9787ef31-fd7b-4eff-ba71-72d580f11f55",
                      "podName": "default_procname",
                      "clusterId": "CONFIG_FILE",
                      "nameSpace": "CONFIG_FILE",
                      "category": "LTS"
                  },
                  "line_num": "1595659490239433659"
              },
              {
                  "content": "2020-07-25/14:44:48 this <HighLightTag>log</HighLightTag> is Error NO 7\n",
                  "labels": {
                      "hostName": "ecs-kwxtest",
                      "hostIP": "192.168.0.156",
                      "appName": "default_appname",
                      "containerName": "CONFIG_FILE",
                      "clusterName": "CONFIG_FILE",
                      "hostId": "9787ef31-fd7b-4eff-ba71-72d580f11f55",
                      "podName": "default_procname",
                      "clusterId": "CONFIG_FILE",
                      "nameSpace": "CONFIG_FILE",
                      "category": "LTS"
                  },
                  "line_num": "1595659490239433660"
              },
              {
                  "content": "2020-07-25/14:44:49 this <HighLightTag>log</HighLightTag> is Error NO 8\n",
                  "labels": {
                      "hostName": "ecs-kwxtest",
                      "hostIP": "192.168.0.156",
                      "appName": "default_appname",
                      "containerName": "CONFIG_FILE",
                      "clusterName": "CONFIG_FILE",
                      "hostId": "9787ef31-fd7b-4eff-ba71-72d580f11f55",
                      "podName": "default_procname",
                      "clusterId": "CONFIG_FILE",
                      "nameSpace": "CONFIG_FILE",
                      "category": "LTS"
                  },
                  "line_num": "1595659490239433661"
              }
          ]
      }

-  For a pagination query (Assume that the search starts from the log event containing **NO 5** and the log events containing **NO 8**, **NO 7**, and **NO 6** are the target log events):

   .. code-block::

      {
          "count": 32,
          "logs": [
              {
                  "content": "2020-07-25/14:44:49 this <HighLightTag>log</HighLightTag> is Error NO 8\n",
                  "labels": {
                      "hostName": "ecs-kwxtest",
                      "hostIP": "192.168.0.156",
                      "appName": "default_appname",
                      "containerName": "CONFIG_FILE",
                      "clusterName": "CONFIG_FILE",
                      "hostId": "9787ef31-fd7b-4eff-ba71-72d580f11f55",
                      "podName": "default_procname",
                      "clusterId": "CONFIG_FILE",
                      "nameSpace": "CONFIG_FILE",
                      "category": "LTS"
                  },
                  "line_num": "1595659490239433661"
              },
              {
                  "content": "2020-07-25/14:44:48 this <HighLightTag>log</HighLightTag> is Error NO 7\n",
                  "labels": {
                      "hostName": "ecs-kwxtest",
                      "hostIP": "192.168.0.156",
                      "appName": "default_appname",
                      "containerName": "CONFIG_FILE",
                      "clusterName": "CONFIG_FILE",
                      "hostId": "9787ef31-fd7b-4eff-ba71-72d580f11f55",
                      "podName": "default_procname",
                      "clusterId": "CONFIG_FILE",
                      "nameSpace": "CONFIG_FILE",
                      "category": "LTS"
                  },
                  "line_num": "1595659490239433660"
              },
              {
                  "content": "2020-07-25/14:44:47 this <HighLightTag>log</HighLightTag> is Error NO 6\n",
                  "labels": {
                      "hostName": "ecs-kwxtest",
                      "hostIP": "192.168.0.156",
                      "appName": "default_appname",
                      "containerName": "CONFIG_FILE",
                      "clusterName": "CONFIG_FILE",
                      "hostId": "9787ef31-fd7b-4eff-ba71-72d580f11f55",
                      "podName": "default_procname",
                      "clusterId": "CONFIG_FILE",
                      "nameSpace": "CONFIG_FILE",
                      "category": "LTS"
                  },
                  "line_num": "1595659490239433659"
              }
          ]
      }

-  For a pagination query (Assume that the search starts from the log event containing **NO 5** and the log events containing **NO 2**, **NO 3**, and **NO 4** are the target log events):

   .. code-block::

      {
          "count": 32,
          "logs": [
              {
                  "content": "2020-07-25/14:44:43 this <HighLightTag>log</HighLightTag> is Error NO 2\n",
                  "labels": {
                      "hostName": "ecs-kwxtest",
                      "hostIP": "192.168.0.156",
                      "appName": "default_appname",
                      "containerName": "CONFIG_FILE",
                      "clusterName": "CONFIG_FILE",
                      "hostId": "9787ef31-fd7b-4eff-ba71-72d580f11f55",
                      "podName": "default_procname",
                      "clusterId": "CONFIG_FILE",
                      "nameSpace": "CONFIG_FILE",
                      "category": "LTS"
                  },
                  "line_num": "1595659490239433655"
              },
              {
                  "content": "2020-07-25/14:44:44 this <HighLightTag>log</HighLightTag> is Error NO 3\n",
                  "labels": {
                      "hostName": "ecs-kwxtest",
                      "hostIP": "192.168.0.156",
                      "appName": "default_appname",
                      "containerName": "CONFIG_FILE",
                      "clusterName": "CONFIG_FILE",
                      "hostId": "9787ef31-fd7b-4eff-ba71-72d580f11f55",
                      "podName": "default_procname",
                      "clusterId": "CONFIG_FILE",
                      "nameSpace": "CONFIG_FILE",
                      "category": "LTS"
                  },
                  "line_num": "1595659490239433656"
              },
              {
                  "content": "2020-07-25/14:44:45 this <HighLightTag>log</HighLightTag> is Error NO 4\n",
                  "labels": {
                      "hostName": "ecs-kwxtest",
                      "hostIP": "192.168.0.156",
                      "appName": "default_appname",
                      "containerName": "CONFIG_FILE",
                      "clusterName": "CONFIG_FILE",
                      "hostId": "9787ef31-fd7b-4eff-ba71-72d580f11f55",
                      "podName": "default_procname",
                      "clusterId": "CONFIG_FILE",
                      "nameSpace": "CONFIG_FILE",
                      "category": "LTS"
                  },
                  "line_num": "1595659490239433657"
              }
          ]
      }

-  For a pagination query (Assume that the search starts from the log event containing **NO 5** and the log events containing **NO 4**, **NO 3**, and **NO 2** are the target log events):

   .. code-block::

      {
          "count": 32,
          "logs": [
              {
                  "content": "2020-07-25/14:44:45 this <HighLightTag>log</HighLightTag> is Error NO 4\n",
                  "labels": {
                      "hostName": "ecs-kwxtest",
                      "hostIP": "192.168.0.156",
                      "appName": "default_appname",
                      "containerName": "CONFIG_FILE",
                      "clusterName": "CONFIG_FILE",
                      "hostId": "9787ef31-fd7b-4eff-ba71-72d580f11f55",
                      "podName": "default_procname",
                      "clusterId": "CONFIG_FILE",
                      "nameSpace": "CONFIG_FILE",
                      "category": "LTS"
                  },
                  "line_num": "1595659490239433657"
              },
              {
                  "content": "2020-07-25/14:44:44 this <HighLightTag>log</HighLightTag> is Error NO 3\n",
                  "labels": {
                      "hostName": "ecs-kwxtest",
                      "hostIP": "192.168.0.156",
                      "appName": "default_appname",
                      "containerName": "CONFIG_FILE",
                      "clusterName": "CONFIG_FILE",
                      "hostId": "9787ef31-fd7b-4eff-ba71-72d580f11f55",
                      "podName": "default_procname",
                      "clusterId": "CONFIG_FILE",
                      "nameSpace": "CONFIG_FILE",
                      "category": "LTS"
                  },
                  "line_num": "1595659490239433656"
              },
              {
                  "content": "2020-07-25/14:44:43 this <HighLightTag>log</HighLightTag> is Error NO 2\n",
                  "labels": {
                      "hostName": "ecs-kwxtest",
                      "hostIP": "192.168.0.156",
                      "appName": "default_appname",
                      "containerName": "CONFIG_FILE",
                      "clusterName": "CONFIG_FILE",
                      "hostId": "9787ef31-fd7b-4eff-ba71-72d580f11f55",
                      "podName": "default_procname",
                      "clusterId": "CONFIG_FILE",
                      "nameSpace": "CONFIG_FILE",
                      "category": "LTS"
                  },
                  "line_num": "1595659490239433655"
              }
          ]
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
     "error_msg" : "Failed to query lts log"
   }

Status Codes
------------

+-------------+--------------------------------------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                                                    |
+=============+================================================================================================================================+
| 200         | The request is successful.                                                                                                     |
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
