:original_name: CreateStructConfig.html

.. _CreateStructConfig:

Creating Structuring Configurations (Recommended)
=================================================

Function
--------

This API is used to create structuring configurations using a structuring template, which facilitates parameter extraction and simplifies the parameter structure.

A user can call this API only once per second.

URI
---

POST /v3/{project_id}/lts/struct/template

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

   +-----------------+-----------------+-----------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                        | Description                                                                                                                                                                                                                                                                                                    |
   +=================+=================+=============================================================================+================================================================================================================================================================================================================================================================================================================+
   | log_group_id    | Yes             | String                                                                      | Log group ID. For details about how to obtain a log group ID, see :ref:`Obtaining the Project ID, Account ID, Log Group ID, and Log Stream ID <lts_api_0006>`.                                                                                                                                                 |
   |                 |                 |                                                                             |                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                                                                             | Minimum: **36**                                                                                                                                                                                                                                                                                                |
   |                 |                 |                                                                             |                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                                                                             | Maximum: **36**                                                                                                                                                                                                                                                                                                |
   +-----------------+-----------------+-----------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_stream_id   | Yes             | String                                                                      | Log stream ID. For details about how to obtain a log stream ID, see :ref:`Obtaining the Project ID, Account ID, Log Group ID, and Log Stream ID <lts_api_0006>`.                                                                                                                                               |
   |                 |                 |                                                                             |                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                                                                             | Minimum: **36**                                                                                                                                                                                                                                                                                                |
   |                 |                 |                                                                             |                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                                                                             | Maximum: **36**                                                                                                                                                                                                                                                                                                |
   +-----------------+-----------------+-----------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | template_id     | Yes             | String                                                                      | Template ID. When the system template is used, the current attribute can be empty.                                                                                                                                                                                                                             |
   |                 |                 |                                                                             |                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                                                                             | Minimum: **0**                                                                                                                                                                                                                                                                                                 |
   |                 |                 |                                                                             |                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                                                                             | Maximum: **36**                                                                                                                                                                                                                                                                                                |
   +-----------------+-----------------+-----------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | template_name   | Yes             | String                                                                      | Template name, which cannot be empty and will be verified.                                                                                                                                                                                                                                                     |
   |                 |                 |                                                                             |                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                                                                             | Minimum: **1**                                                                                                                                                                                                                                                                                                 |
   |                 |                 |                                                                             |                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                                                                             | Maximum: **64**                                                                                                                                                                                                                                                                                                |
   +-----------------+-----------------+-----------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | template_type   | Yes             | String                                                                      | Type of the template. The value can be **built_in** (system templates) or **custom** (custom templates). For details about system template types, see section "Log Search and Analysis" > "Cloud Structuring Parsing" > "Structuring Templates" in the LTS User Guide.                                         |
   +-----------------+-----------------+-----------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | demo_fields     | No              | Array of :ref:`FieldModel <createstructconfig__request_fieldmodel>` objects | Example field array. You only need to enter the fields whose status is different from that of **is_analysis** in the template.                                                                                                                                                                                 |
   +-----------------+-----------------+-----------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tag_fields      | No              | Array of :ref:`FieldModel <createstructconfig__request_fieldmodel>` objects | Tag field array. You only need to enter the fields whose status is different from that of **is_analysis** in the template.                                                                                                                                                                                     |
   +-----------------+-----------------+-----------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | quick_analysis  | No              | Boolean                                                                     | Indicates whether to enable quick analysis for **demo_fields** and **tag_fields**. If this parameter is set to **true**, quick analysis is enabled for all fields. If this parameter is left blank or set to **false**, **is_analysis** in the template is used to determine whether to enable quick analysis. |
   +-----------------+-----------------+-----------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _createstructconfig__request_fieldmodel:

.. table:: **Table 4** FieldModel

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                        |
   +=================+=================+=================+====================================================================================+
   | field_name      | Yes             | String          | Field name. A log event can be split into multiple fields with customizable names. |
   |                 |                 |                 |                                                                                    |
   |                 |                 |                 | Minimum: **1**                                                                     |
   |                 |                 |                 |                                                                                    |
   |                 |                 |                 | Maximum: **64**                                                                    |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------+
   | is_analysis     | No              | Boolean         | Whether quick analysis is enabled.                                                 |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 400**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

-  Creating an ELB system template

   .. code-block:: text

      POST https://{endpoint}/v3/{project_id}/lts/struct/template

      {
        "log_group_id" : "17f23e52-a23d-46e0-8bc5-xxxxxxxxxxxx",
        "log_stream_id" : "b4d56d47-b4c4-453e-9047-xxxxxxxxxxxx",
        "demo_fields" : [ {
          "field_name" : "msec",
          "is_analysis" : false
        }, {
          "field_name" : "access_log_topic_id",
          "is_analysis" : false
        }, {
          "field_name" : "time_iso8601",
          "is_analysis" : false
        }, {
          "field_name" : "log_ver",
          "is_analysis" : true
        }, {
          "field_name" : "remote_addr",
          "is_analysis" : true
        }, {
          "field_name" : "remote_port",
          "is_analysis" : false
        }, {
          "field_name" : "status",
          "is_analysis" : false
        }, {
          "field_name" : "request_method",
          "is_analysis" : false
        }, {
          "field_name" : "scheme",
          "is_analysis" : true
        }, {
          "field_name" : "host",
          "is_analysis" : true
        }, {
          "field_name" : "router_request_uri",
          "is_analysis" : true
        }, {
          "field_name" : "server_protocol",
          "is_analysis" : true
        }, {
          "field_name" : "request_length",
          "is_analysis" : true
        }, {
          "field_name" : "bytes_sent",
          "is_analysis" : false
        }, {
          "field_name" : "body_bytes_sent",
          "is_analysis" : false
        }, {
          "field_name" : "request_time",
          "is_analysis" : false
        }, {
          "field_name" : "upstream_status",
          "is_analysis" : false
        }, {
          "field_name" : "upstream_connect_time",
          "is_analysis" : false
        }, {
          "field_name" : "upstream_header_time",
          "is_analysis" : false
        }, {
          "field_name" : "upstream_response_time",
          "is_analysis" : false
        }, {
          "field_name" : "upstream_addr",
          "is_analysis" : false
        }, {
          "field_name" : "http_user_agent",
          "is_analysis" : false
        }, {
          "field_name" : "http_referer",
          "is_analysis" : false
        }, {
          "field_name" : "http_x_forwarded_for",
          "is_analysis" : false
        }, {
          "field_name" : "lb_name",
          "is_analysis" : false
        }, {
          "field_name" : "listener_name",
          "is_analysis" : false
        }, {
          "field_name" : "listener_id",
          "is_analysis" : false
        }, {
          "field_name" : "pool_name",
          "is_analysis" : false
        }, {
          "field_name" : "member_name",
          "is_analysis" : false
        }, {
          "field_name" : "tenant_id",
          "is_analysis" : false
        }, {
          "field_name" : "eip_address",
          "is_analysis" : false
        }, {
          "field_name" : "eip_port",
          "is_analysis" : false
        }, {
          "field_name" : "upstream_addr_priv",
          "is_analysis" : false
        }, {
          "field_name" : "certificate_id",
          "is_analysis" : false
        }, {
          "field_name" : "ssl_protocol",
          "is_analysis" : false
        }, {
          "field_name" : "ssl_cipher",
          "is_analysis" : false
        }, {
          "field_name" : "sni_domain_name",
          "is_analysis" : false
        }, {
          "field_name" : "tcpinfo_rtt",
          "is_analysis" : false
        } ],
        "tag_fields" : [ {
          "field_name" : "hostIP",
          "is_analysis" : true
        } ],
        "template_type" : "built_in",
        "template_name" : "ELB",
        "template_id" : "",
        "quick_analysis" : false
      }

-  Creating a VPC system template

   .. code-block:: text

      POST https://{endpoint}/v3/{project_id}/lts/struct/template

      {
        "log_group_id" : "17f23e52-a23d-46e0-8bc5-xxxxxxxxxxxx",
        "log_stream_id" : "b4d56d47-b4c4-453e-9047-xxxxxxxxxxxx",
        "demo_fields" : [ {
          "field_name" : "version",
          "is_analysis" : false
        }, {
          "field_name" : "project_id",
          "is_analysis" : true
        }, {
          "field_name" : "interface_id",
          "is_analysis" : false
        }, {
          "field_name" : "srcaddr",
          "is_analysis" : true
        }, {
          "field_name" : "dstaddr",
          "is_analysis" : true
        }, {
          "field_name" : "srcport",
          "is_analysis" : false
        }, {
          "field_name" : "dstport",
          "is_analysis" : false
        }, {
          "field_name" : "protocol",
          "is_analysis" : false
        }, {
          "field_name" : "packets",
          "is_analysis" : false
        }, {
          "field_name" : "bytes",
          "is_analysis" : false
        }, {
          "field_name" : "start",
          "is_analysis" : false
        }, {
          "field_name" : "end",
          "is_analysis" : false
        }, {
          "field_name" : "action",
          "is_analysis" : true
        }, {
          "field_name" : "log_status",
          "is_analysis" : true
        } ],
        "tag_fields" : [ {
          "field_name" : "hostIP",
          "is_analysis" : true
        } ],
        "template_type" : "built_in",
        "template_name" : "VPC",
        "template_id" : "",
        "quick_analysis" : false
      }

Example Responses
-----------------

**Status code: 201**

The request is successful.

.. code-block::

    none

**Status code: 400**

Invalid request. Modify the request based on the description in **error_msg** before a retry.

.. code-block::

   {
     "error_code" : "LTS.2014",
     "error_msg" : "template_id is invalid!"
   }

**Status code: 500**

The server has received the request but encountered an internal error.

.. code-block::

   {
     "error_code" : "LTS.2014",
     "error_msg" : "Failed to create struct config."
   }

Status Codes
------------

+-------------+-----------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                   |
+=============+===============================================================================================+
| 201         | The request is successful.                                                                    |
+-------------+-----------------------------------------------------------------------------------------------+
| 400         | Invalid request. Modify the request based on the description in **error_msg** before a retry. |
+-------------+-----------------------------------------------------------------------------------------------+
| 500         | The server has received the request but encountered an internal error.                        |
+-------------+-----------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
