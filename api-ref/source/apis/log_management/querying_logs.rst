:original_name: ListLogs.html

.. _ListLogs:

Querying Logs
=============

Function
--------

This API is used to query logs in a specified log stream.

URI
---

POST /v2/{project_id}/groups/{log_group_id}/streams/{log_stream_id}/content/query

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                      |
   +=================+=================+=================+==================================================================================================================================================================+
   | project_id      | Yes             | String          | Project ID. For details about how to obtain a project ID, see :ref:`Obtaining the Project ID, Account ID, Log Group ID, and Log Stream ID <lts_api_0006>`.       |
   |                 |                 |                 |                                                                                                                                                                  |
   |                 |                 |                 | Minimum: **32**                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                  |
   |                 |                 |                 | Maximum: **32**                                                                                                                                                  |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_group_id    | Yes             | String          | Log group ID. For details about how to obtain a log group ID, see :ref:`Obtaining the Project ID, Account ID, Log Group ID, and Log Stream ID <lts_api_0006>`.   |
   |                 |                 |                 |                                                                                                                                                                  |
   |                 |                 |                 | Minimum: **36**                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                  |
   |                 |                 |                 | Maximum: **36**                                                                                                                                                  |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_stream_id   | Yes             | String          | Log stream ID. For details about how to obtain a log stream ID, see :ref:`Obtaining the Project ID, Account ID, Log Group ID, and Log Stream ID <lts_api_0006>`. |
   |                 |                 |                 |                                                                                                                                                                  |
   |                 |                 |                 | Minimum: **36**                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                  |
   |                 |                 |                 | Maximum: **36**                                                                                                                                                  |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   +-----------------+-----------------+--------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type               | Description                                                                                                                                                                                                                                                                                                                                                                                                                  |
   +=================+=================+====================+==============================================================================================================================================================================================================================================================================================================================================================================================================================+
   | start_time      | Yes             | String             | UTC start time of the search window (in milliseconds).                                                                                                                                                                                                                                                                                                                                                                       |
   |                 |                 |                    |                                                                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                    | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                    |                                                                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                    |    Maximum query time range: 180 days                                                                                                                                                                                                                                                                                                                                                                                        |
   +-----------------+-----------------+--------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | end_time        | Yes             | String             | UTC end time of the search window (in milliseconds).                                                                                                                                                                                                                                                                                                                                                                         |
   |                 |                 |                    |                                                                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                    | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                    |                                                                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                    |    Maximum query time range: 180 days                                                                                                                                                                                                                                                                                                                                                                                        |
   +-----------------+-----------------+--------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | labels          | No              | Map<String,String> | Filter criteria, which vary between log sources.                                                                                                                                                                                                                                                                                                                                                                             |
   +-----------------+-----------------+--------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | keywords        | No              | String             | Keyword used for log search. A keyword is a word between two adjacent delimiters, for example, error.                                                                                                                                                                                                                                                                                                                        |
   +-----------------+-----------------+--------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | line_num        | No              | String             | Sequence number of a log event. This parameter is not required for the first query, but is required for subsequent pagination queries. The value can be obtained from the response of the last query. The value of **line_num** should be between the values of **start_time** and **end_time**. If the custom time function is enabled, you need to use both this field and the **time** field to perform pagination query. |
   |                 |                 |                    |                                                                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                    | Minimum: **19**                                                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                    |                                                                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                    | Maximum: **19**                                                                                                                                                                                                                                                                                                                                                                                                              |
   +-----------------+-----------------+--------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | \__time_\_      | No              | String             | If the custom time function is enabled, use both this field and the **line_num** field for pagination queries. The parameter values can be obtained from the returned information of the last query.                                                                                                                                                                                                                         |
   +-----------------+-----------------+--------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | is_desc         | No              | Boolean            | Whether the search order is descending. The default value is **false** (ascending). You can also set the value to **true** (descending).                                                                                                                                                                                                                                                                                     |
   +-----------------+-----------------+--------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | search_type     | No              | String             | The value is **init** (default value) for the first query, or **forwards** or **backwards** for a pagination query. This parameter is used together with **is_desc** for pagination queries.The value can be **forwards** or **backwards**.                                                                                                                                                                                  |
   +-----------------+-----------------+--------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer            | Number of logs to be queried each time. The value is **50** when this parameter is not set. You are advised to set this parameter to **100**.                                                                                                                                                                                                                                                                                |
   |                 |                 |                    |                                                                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                    | Minimum: **1**                                                                                                                                                                                                                                                                                                                                                                                                               |
   |                 |                 |                    |                                                                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                    | Maximum: **5000**                                                                                                                                                                                                                                                                                                                                                                                                            |
   +-----------------+-----------------+--------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | highlight       | No              | Boolean            | Whether the keyword is highlighted. The default value is **true** (highlighted). You can also set the value to **false** (not highlighted).                                                                                                                                                                                                                                                                                  |
   +-----------------+-----------------+--------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | is_count        | No              | Boolean            | Whether the number of log events is counted. The default value is **false** (not counted). You can also set the value to **true** (counted).                                                                                                                                                                                                                                                                                 |
   +-----------------+-----------------+--------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | is_iterative    | No              | Boolean            | Whether the log query is iterative. The default value is **false** (not iterative). You can also set the value to **true** (iterative).                                                                                                                                                                                                                                                                                      |
   +-----------------+-----------------+--------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------------+----------------------------------------------------------------------+------------------------------------------+
   | Parameter       | Type                                                                 | Description                              |
   +=================+======================================================================+==========================================+
   | logs            | Array of :ref:`LogContents <listlogs__response_logcontents>` objects | Log information.                         |
   +-----------------+----------------------------------------------------------------------+------------------------------------------+
   | count           | Integer                                                              | Number of logs.                          |
   +-----------------+----------------------------------------------------------------------+------------------------------------------+
   | isQueryComplete | Boolean                                                              | Indicates whether the query is complete. |
   +-----------------+----------------------------------------------------------------------+------------------------------------------+

.. _listlogs__response_logcontents:

.. table:: **Table 5** LogContents

   +-----------+--------------------+---------------------------------------------------------------------------+
   | Parameter | Type               | Description                                                               |
   +===========+====================+===========================================================================+
   | content   | String             | Raw log data.                                                             |
   +-----------+--------------------+---------------------------------------------------------------------------+
   | line_num  | String             | Sequence number of a log line.                                            |
   +-----------+--------------------+---------------------------------------------------------------------------+
   | labels    | Map<String,String> | Labels contained in a log event. The labels vary depending on log events. |
   +-----------+--------------------+---------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 401**

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 8** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 9** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

-  Querying logs

   .. code-block:: text

      POST https://{endpoint}/v2/{project_id}/groups/{log_group_id}/streams/{log_stream_id}/content/query

      {
        "start_time" : 1595659200000,
        "end_time" : 1595659500000,
        "labels" : {
          "hostName" : "ecs-kwxtest"
        },
        "keywords" : "log",
        "limit" : 10,
        "is_count" : true
      }

-  Querying logs for the first time

   .. code-block:: text

      POST v2/{project_id}/groups/{log_group_id}/streams/{log_stream_id}/content/query

      {
        "start_time" : 1595659200000,
        "end_time" : 1595659500000,
        "labels" : {
          "hostName" : "ecs-kwxtest"
        },
        "keywords" : "log",
        "line_num" : "1595659490239433658",
        "is_desc" : "false",
        "search_type" : "forwards",
        "limit" : "3",
        "is_count" : true
      }

-  For a pagination query (Assume that the search starts from the log event containing **NO 5**. Log events containing **NO 6**, **NO 7**, and **NO 8** are the target log events):

   .. code-block:: text

      POST v2/{project_id}/groups/{log_group_id}/streams/{log_stream_id}/content/query '

      {
        "start_time" : 1595659200000,
        "end_time" : 1595659500000,
        "labels" : {
          "hostName" : "ecs-kwxtest"
        },
        "keywords" : "log",
        "line_num" : "1595659490239433658",
        "is_desc" : "true",
        "search_type" : "backwards",
        "limit" : "3",
        "is_count" : true
      }

-  For a pagination query (Assume that the search starts from the log event containing **NO 5**. Log events containing **NO 8**, **NO 7**, and **NO 6** are the target log events):

   .. code-block:: text

      POST v2/{project_id}/groups/{log_group_id}/streams/{log_stream_id}/content/query

      {
        "start_time" : 1595659200000,
        "end_time" : 1595659500000,
        "labels" : {
          "hostName" : "ecs-kwxtest"
        },
        "keywords" : "log",
        "line_num" : "1595659490239433658",
        "is_desc" : "false",
        "search_type" : "backwards",
        "limit" : "3",
        "is_count" : true
      }

-  For a pagination query (Assume that the search starts from the log event containing **NO 5**. Log events containing **NO 2**, **NO 3**, and **NO 4** are the target log events):

   .. code-block:: text

      POST v2/{project_id}/groups/{log_group_id}/streams/{log_stream_id}/content/query '

      {
        "start_time" : 1595659200000,
        "end_time" : 1595659500000,
        "labels" : {
          "hostName" : "ecs-kwxtest"
        },
        "keywords" : "log",
        "line_num" : "1595659490239433658",
        "is_desc" : "true",
        "search_type" : "forwards",
        "limit" : "3",
        "is_count" : true
      }

Example Responses
-----------------

**Status code: 200**

The request is successful.

-  Querying logs for the first time

   .. code-block::

      {
        "count" : 32,
        "logs" : [ {
          "content" : "2020-07-25/14:44:42 this <HighLightTag>log</HighLightTag> is Error NO 1",
          "labels" : {
            "hostName" : "ecs-kwxtest",
            "hostIP" : "192.168.0.156",
            "appName" : "default_appname",
            "containerName" : "CONFIG_FILE",
            "clusterName" : "CONFIG_FILE",
            "hostId" : "9787ef31-fd7b-4eff-ba71-72d580f11f55",
            "podName" : "default_procname",
            "clusterId" : "CONFIG_FILE",
            "nameSpace" : "CONFIG_FILE",
            "category" : "LTS"
          },
          "line_num" : "1595659490239433654"
        }, {
          "content" : "2020-07-25/14:44:43 this <HighLightTag>log</HighLightTag> is Error NO 2",
          "labels" : {
            "hostName" : "ecs-kwxtest",
            "hostIP" : "192.168.0.156",
            "appName" : "default_appname",
            "containerName" : "CONFIG_FILE",
            "clusterName" : "CONFIG_FILE",
            "hostId" : "9787ef31-fd7b-4eff-ba71-72d580f11f55",
            "podName" : "default_procname",
            "clusterId" : "CONFIG_FILE",
            "nameSpace" : "CONFIG_FILE",
            "category" : "LTS"
          },
          "line_num" : "1595659490239433655"
        }, {
          "content" : "2020-07-25/14:44:44 this <HighLightTag>log</HighLightTag> is Error NO 3",
          "labels" : {
            "hostName" : "ecs-kwxtest",
            "hostIP" : "192.168.0.156",
            "appName" : "default_appname",
            "containerName" : "CONFIG_FILE",
            "clusterName" : "CONFIG_FILE",
            "hostId" : "9787ef31-fd7b-4eff-ba71-72d580f11f55",
            "podName" : "default_procname",
            "clusterId" : "CONFIG_FILE",
            "nameSpace" : "CONFIG_FILE",
            "category" : "LTS"
          },
          "line_num" : "1595659490239433656"
        }, {
          "content" : "2020-07-25/14:44:45 this <HighLightTag>log</HighLightTag> is Error NO 4",
          "labels" : {
            "hostName" : "ecs-kwxtest",
            "hostIP" : "192.168.0.156",
            "appName" : "default_appname",
            "containerName" : "CONFIG_FILE",
            "clusterName" : "CONFIG_FILE",
            "hostId" : "9787ef31-fd7b-4eff-ba71-72d580f11f55",
            "podName" : "default_procname",
            "clusterId" : "CONFIG_FILE",
            "nameSpace" : "CONFIG_FILE",
            "category" : "LTS"
          },
          "line_num" : "1595659490239433657"
        }, {
          "content" : "2020-07-25/14:44:46 this <HighLightTag>log</HighLightTag> is Error NO 5",
          "labels" : {
            "hostName" : "ecs-kwxtest",
            "hostIP" : "192.168.0.156",
            "appName" : "default_appname",
            "containerName" : "CONFIG_FILE",
            "clusterName" : "CONFIG_FILE",
            "hostId" : "9787ef31-fd7b-4eff-ba71-72d580f11f55",
            "podName" : "default_procname",
            "clusterId" : "CONFIG_FILE",
            "nameSpace" : "CONFIG_FILE",
            "category" : "LTS"
          },
          "line_num" : "1595659490239433658"
        }, {
          "content" : "2020-07-25/14:44:47 this <HighLightTag>log</HighLightTag> is Error NO 6",
          "labels" : {
            "hostName" : "ecs-kwxtest",
            "hostIP" : "192.168.0.156",
            "appName" : "default_appname",
            "containerName" : "CONFIG_FILE",
            "clusterName" : "CONFIG_FILE",
            "hostId" : "9787ef31-fd7b-4eff-ba71-72d580f11f55",
            "podName" : "default_procname",
            "clusterId" : "CONFIG_FILE",
            "nameSpace" : "CONFIG_FILE",
            "category" : "LTS"
          },
          "line_num" : "1595659490239433659"
        }, {
          "content" : "2020-07-25/14:44:48 this <HighLightTag>log</HighLightTag> is Error NO 7",
          "labels" : {
            "hostName" : "ecs-kwxtest",
            "hostIP" : "192.168.0.156",
            "appName" : "default_appname",
            "containerName" : "CONFIG_FILE",
            "clusterName" : "CONFIG_FILE",
            "hostId" : "9787ef31-fd7b-4eff-ba71-72d580f11f55",
            "podName" : "default_procname",
            "clusterId" : "CONFIG_FILE",
            "nameSpace" : "CONFIG_FILE",
            "category" : "LTS"
          },
          "line_num" : "1595659490239433660"
        }, {
          "content" : "2020-07-25/14:44:49 this <HighLightTag>log</HighLightTag> is Error NO 8",
          "labels" : {
            "hostName" : "ecs-kwxtest",
            "hostIP" : "192.168.0.156",
            "appName" : "default_appname",
            "containerName" : "CONFIG_FILE",
            "clusterName" : "CONFIG_FILE",
            "hostId" : "9787ef31-fd7b-4eff-ba71-72d580f11f55",
            "podName" : "default_procname",
            "clusterId" : "CONFIG_FILE",
            "nameSpace" : "CONFIG_FILE",
            "category" : "LTS"
          },
          "line_num" : "1595659490239433661"
        }, {
          "content" : "2020-07-25/14:44:50 this <HighLightTag>log</HighLightTag> is Error NO 9",
          "labels" : {
            "hostName" : "ecs-kwxtest",
            "hostIP" : "192.168.0.156",
            "appName" : "default_appname",
            "containerName" : "CONFIG_FILE",
            "clusterName" : "CONFIG_FILE",
            "hostId" : "9787ef31-fd7b-4eff-ba71-72d580f11f55",
            "podName" : "default_procname",
            "clusterId" : "CONFIG_FILE",
            "nameSpace" : "CONFIG_FILE",
            "category" : "LTS"
          },
          "line_num" : "1595659490839420574"
        }, {
          "content" : "2020-07-25/14:44:51 this <HighLightTag>log</HighLightTag> is Error NO 10",
          "labels" : {
            "hostName" : "ecs-kwxtest",
            "hostIP" : "192.168.0.156",
            "appName" : "default_appname",
            "containerName" : "CONFIG_FILE",
            "clusterName" : "CONFIG_FILE",
            "hostId" : "9787ef31-fd7b-4eff-ba71-72d580f11f55",
            "podName" : "default_procname",
            "clusterId" : "CONFIG_FILE",
            "nameSpace" : "CONFIG_FILE",
            "category" : "LTS"
          },
          "line_num" : "1595659491839412667"
        } ]
      }

-  For a pagination query (Assume that the search starts from the log event containing **NO 5**. Log events containing **NO 6**, **NO 7**, and **NO 8** are the target log events):

   .. code-block::

      {
        "count" : 32,
        "logs" : [ {
          "content" : "2020-07-25/14:44:47 this <HighLightTag>log</HighLightTag> is Error NO 6",
          "labels" : {
            "hostName" : "ecs-kwxtest",
            "hostIP" : "192.168.0.156",
            "appName" : "default_appname",
            "containerName" : "CONFIG_FILE",
            "clusterName" : "CONFIG_FILE",
            "hostId" : "9787ef31-fd7b-4eff-ba71-72d580f11f55",
            "podName" : "default_procname",
            "clusterId" : "CONFIG_FILE",
            "nameSpace" : "CONFIG_FILE",
            "category" : "LTS"
          },
          "line_num" : "1595659490239433659"
        }, {
          "content" : "2020-07-25/14:44:48 this <HighLightTag>log</HighLightTag> is Error NO 7",
          "labels" : {
            "hostName" : "ecs-kwxtest",
            "hostIP" : "192.168.0.156",
            "appName" : "default_appname",
            "containerName" : "CONFIG_FILE",
            "clusterName" : "CONFIG_FILE",
            "hostId" : "9787ef31-fd7b-4eff-ba71-72d580f11f55",
            "podName" : "default_procname",
            "clusterId" : "CONFIG_FILE",
            "nameSpace" : "CONFIG_FILE",
            "category" : "LTS"
          },
          "line_num" : "1595659490239433660"
        }, {
          "content" : "2020-07-25/14:44:49 this <HighLightTag>log</HighLightTag> is Error NO 8",
          "labels" : {
            "hostName" : "ecs-kwxtest",
            "hostIP" : "192.168.0.156",
            "appName" : "default_appname",
            "containerName" : "CONFIG_FILE",
            "clusterName" : "CONFIG_FILE",
            "hostId" : "9787ef31-fd7b-4eff-ba71-72d580f11f55",
            "podName" : "default_procname",
            "clusterId" : "CONFIG_FILE",
            "nameSpace" : "CONFIG_FILE",
            "category" : "LTS"
          },
          "line_num" : "1595659490239433661"
        } ]
      }

-  For a pagination query (Assume that the search starts from the log event containing **NO 5**. Log events containing **NO 8**, **NO 7**, and **NO 6** are the target log events):

   .. code-block::

      {
        "count" : 32,
        "logs" : [ {
          "content" : "2020-07-25/14:44:49 this <HighLightTag>log</HighLightTag> is Error NO 8",
          "labels" : {
            "hostName" : "ecs-kwxtest",
            "hostIP" : "192.168.0.156",
            "appName" : "default_appname",
            "containerName" : "CONFIG_FILE",
            "clusterName" : "CONFIG_FILE",
            "hostId" : "9787ef31-fd7b-4eff-ba71-72d580f11f55",
            "podName" : "default_procname",
            "clusterId" : "CONFIG_FILE",
            "nameSpace" : "CONFIG_FILE",
            "category" : "LTS"
          },
          "line_num" : "1595659490239433661"
        }, {
          "content" : "2020-07-25/14:44:48 this <HighLightTag>log</HighLightTag> is Error NO 7",
          "labels" : {
            "hostName" : "ecs-kwxtest",
            "hostIP" : "192.168.0.156",
            "appName" : "default_appname",
            "containerName" : "CONFIG_FILE",
            "clusterName" : "CONFIG_FILE",
            "hostId" : "9787ef31-fd7b-4eff-ba71-72d580f11f55",
            "podName" : "default_procname",
            "clusterId" : "CONFIG_FILE",
            "nameSpace" : "CONFIG_FILE",
            "category" : "LTS"
          },
          "line_num" : "1595659490239433660"
        }, {
          "content" : "2020-07-25/14:44:47 this <HighLightTag>log</HighLightTag> is Error NO 6",
          "labels" : {
            "hostName" : "ecs-kwxtest",
            "hostIP" : "192.168.0.156",
            "appName" : "default_appname",
            "containerName" : "CONFIG_FILE",
            "clusterName" : "CONFIG_FILE",
            "hostId" : "9787ef31-fd7b-4eff-ba71-72d580f11f55",
            "podName" : "default_procname",
            "clusterId" : "CONFIG_FILE",
            "nameSpace" : "CONFIG_FILE",
            "category" : "LTS"
          },
          "line_num" : "1595659490239433659"
        } ]
      }

-  For a pagination query (Assume that the search starts from the log event containing **NO 5**. Log events containing **NO 2**, **NO 3**, and **NO 4** are the target log events):

   .. code-block::

      {
        "count" : 32,
        "logs" : [ {
          "content" : "2020-07-25/14:44:43 this <HighLightTag>log</HighLightTag> is Error NO 2",
          "labels" : {
            "hostName" : "ecs-kwxtest",
            "hostIP" : "192.168.0.156",
            "appName" : "default_appname",
            "containerName" : "CONFIG_FILE",
            "clusterName" : "CONFIG_FILE",
            "hostId" : "9787ef31-fd7b-4eff-ba71-72d580f11f55",
            "podName" : "default_procname",
            "clusterId" : "CONFIG_FILE",
            "nameSpace" : "CONFIG_FILE",
            "category" : "LTS"
          },
          "line_num" : "1595659490239433655"
        }, {
          "content" : "2020-07-25/14:44:44 this <HighLightTag>log</HighLightTag> is Error NO 3",
          "labels" : {
            "hostName" : "ecs-kwxtest",
            "hostIP" : "192.168.0.156",
            "appName" : "default_appname",
            "containerName" : "CONFIG_FILE",
            "clusterName" : "CONFIG_FILE",
            "hostId" : "9787ef31-fd7b-4eff-ba71-72d580f11f55",
            "podName" : "default_procname",
            "clusterId" : "CONFIG_FILE",
            "nameSpace" : "CONFIG_FILE",
            "category" : "LTS"
          },
          "line_num" : "1595659490239433656"
        }, {
          "content" : "2020-07-25/14:44:45 this <HighLightTag>log</HighLightTag> is Error NO 4",
          "labels" : {
            "hostName" : "ecs-kwxtest",
            "hostIP" : "192.168.0.156",
            "appName" : "default_appname",
            "containerName" : "CONFIG_FILE",
            "clusterName" : "CONFIG_FILE",
            "hostId" : "9787ef31-fd7b-4eff-ba71-72d580f11f55",
            "podName" : "default_procname",
            "clusterId" : "CONFIG_FILE",
            "nameSpace" : "CONFIG_FILE",
            "category" : "LTS"
          },
          "line_num" : "1595659490239433657"
        } ]
      }

-  For a pagination query (Assume that the search starts from the log event containing **NO 5**. Log events containing **NO 4**, **NO 3**, and **NO 2** are the target log events):

   .. code-block::

      {
        "count" : 32,
        "logs" : [ {
          "content" : "2020-07-25/14:44:45 this <HighLightTag>log</HighLightTag> is Error NO 4",
          "labels" : {
            "hostName" : "ecs-kwxtest",
            "hostIP" : "192.168.0.156",
            "appName" : "default_appname",
            "containerName" : "CONFIG_FILE",
            "clusterName" : "CONFIG_FILE",
            "hostId" : "9787ef31-fd7b-4eff-ba71-72d580f11f55",
            "podName" : "default_procname",
            "clusterId" : "CONFIG_FILE",
            "nameSpace" : "CONFIG_FILE",
            "category" : "LTS"
          },
          "line_num" : "1595659490239433657"
        }, {
          "content" : "2020-07-25/14:44:44 this <HighLightTag>log</HighLightTag> is Error NO 3",
          "labels" : {
            "hostName" : "ecs-kwxtest",
            "hostIP" : "192.168.0.156",
            "appName" : "default_appname",
            "containerName" : "CONFIG_FILE",
            "clusterName" : "CONFIG_FILE",
            "hostId" : "9787ef31-fd7b-4eff-ba71-72d580f11f55",
            "podName" : "default_procname",
            "clusterId" : "CONFIG_FILE",
            "nameSpace" : "CONFIG_FILE",
            "category" : "LTS"
          },
          "line_num" : "1595659490239433656"
        }, {
          "content" : "2020-07-25/14:44:43 this <HighLightTag>log</HighLightTag> is Error NO 2",
          "labels" : {
            "hostName" : "ecs-kwxtest",
            "hostIP" : "192.168.0.156",
            "appName" : "default_appname",
            "containerName" : "CONFIG_FILE",
            "clusterName" : "CONFIG_FILE",
            "hostId" : "9787ef31-fd7b-4eff-ba71-72d580f11f55",
            "podName" : "default_procname",
            "clusterId" : "CONFIG_FILE",
            "nameSpace" : "CONFIG_FILE",
            "category" : "LTS"
          },
          "line_num" : "1595659490239433655"
        } ]
      }

**Status code: 400**

Bad request. The request is invalid or the query statement is incorrect. Modify the request based on the description in **error_msg** before a retry.

.. code-block::

   {
     "error_code" : "LTS.0009",
     "error_msg" : "Failed to validate the request body"
   }

**Status code: 401**

AuthFailed. Authentication failed. Check the token and try again.

.. code-block::

   {
     "error_code" : "LTS.0003",
     "error_msg" : "Invalid token"
   }

**Status code: 403**

Forbidden.The request has been rejected.The server has received the request and understood it, but refuses to respond to it. The client should not repeat the request without modifications.

.. code-block::

   {
     "error_code" : "LTS.0001",
     "error_msg" : "Invalid projectId"
   }

**Status code: 500**

InternalServerError.

The server has received the request but encountered an internal error.

.. code-block::

   {
     "error_code" : "LTS.0202",
     "error_msg" : "Failed to query lts log"
   }

Status Codes
------------

+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Status Code                       | Description                                                                                                                                                                                  |
+===================================+==============================================================================================================================================================================================+
| 200                               | The request is successful.                                                                                                                                                                   |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 400                               | Bad request. The request is invalid or the query statement is incorrect. Modify the request based on the description in **error_msg** before a retry.                                        |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 401                               | AuthFailed. Authentication failed. Check the token and try again.                                                                                                                            |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 403                               | Forbidden.The request has been rejected.The server has received the request and understood it, but refuses to respond to it. The client should not repeat the request without modifications. |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 500                               | InternalServerError.                                                                                                                                                                         |
|                                   |                                                                                                                                                                                              |
|                                   | The server has received the request but encountered an internal error.                                                                                                                       |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
