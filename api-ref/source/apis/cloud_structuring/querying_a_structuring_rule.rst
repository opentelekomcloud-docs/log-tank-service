:original_name: lts_api_0041.html

.. _lts_api_0041:

Querying a Structuring Rule
===========================

Function
--------

This API is used to query the structuring rule of a specified log stream.

URI
---

GET /v2/{project_id}/lts/struct/template

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

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                      |
   +=================+=================+=================+==================================================================================================================================================================+
   | logGroupId      | Yes             | String          | Log group ID. For details about how to obtain a log group ID, see :ref:`Obtaining the Project ID, Account ID, Log Group ID, and Log Stream ID <lts_api_0006>`.   |
   |                 |                 |                 |                                                                                                                                                                  |
   |                 |                 |                 | Minimum: **36**                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                  |
   |                 |                 |                 | Maximum: **36**                                                                                                                                                  |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | logStreamId     | Yes             | String          | Log stream ID. For details about how to obtain a log stream ID, see :ref:`Obtaining the Project ID, Account ID, Log Group ID, and Log Stream ID <lts_api_0006>`. |
   |                 |                 |                 |                                                                                                                                                                  |
   |                 |                 |                 | Minimum: **36**                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                  |
   |                 |                 |                 | Maximum: **36**                                                                                                                                                  |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

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

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +--------------+----------------------------------------------------------------------------------------------------+-------------------------------------+
   | Parameter    | Type                                                                                               | Description                         |
   +==============+====================================================================================================+=====================================+
   | demoFields   | Array of :ref:`StructFieldInfoReturn <lts_api_0041__response_structfieldinforeturn>` objects       | Structured field.                   |
   +--------------+----------------------------------------------------------------------------------------------------+-------------------------------------+
   | tagFields    | Array of :ref:`tag_fields_info <lts_api_0041__response_tag_fields_info>` objects                   | Keyword details.                    |
   +--------------+----------------------------------------------------------------------------------------------------+-------------------------------------+
   | demoLog      | String                                                                                             | Sample log event.                   |
   +--------------+----------------------------------------------------------------------------------------------------+-------------------------------------+
   | demoLabel    | String                                                                                             | Attributes of the sample log event. |
   +--------------+----------------------------------------------------------------------------------------------------+-------------------------------------+
   | id           | String                                                                                             | Structuring rule ID.                |
   +--------------+----------------------------------------------------------------------------------------------------+-------------------------------------+
   | logGroupId   | String                                                                                             | Log group ID.                       |
   +--------------+----------------------------------------------------------------------------------------------------+-------------------------------------+
   | rule         | :ref:`ShowStructTemplateRule <lts_api_0041__response_showstructtemplaterule>` object               | Structuring method.                 |
   +--------------+----------------------------------------------------------------------------------------------------+-------------------------------------+
   | cluster_info | :ref:`ShowStructTemplateclusterInfo <lts_api_0041__response_showstructtemplateclusterinfo>` object | Kafka information.                  |
   +--------------+----------------------------------------------------------------------------------------------------+-------------------------------------+
   | logStreamId  | String                                                                                             | Log stream ID.                      |
   +--------------+----------------------------------------------------------------------------------------------------+-------------------------------------+
   | projectId    | String                                                                                             | Project ID.                         |
   +--------------+----------------------------------------------------------------------------------------------------+-------------------------------------+
   | templateName | String                                                                                             | Template name.                      |
   +--------------+----------------------------------------------------------------------------------------------------+-------------------------------------+
   | regex        | String                                                                                             | Regular expression.                 |
   +--------------+----------------------------------------------------------------------------------------------------+-------------------------------------+

.. _lts_api_0041__response_structfieldinforeturn:

.. table:: **Table 5** StructFieldInfoReturn

   ========== ======= ===========================
   Parameter  Type    Description
   ========== ======= ===========================
   fieldName  String  Field name.
   type       String  Field data type.
   content    String  Field content.
   isAnalysis Boolean Whether parsing is enabled.
   index      Integer Field sequence number.
   ========== ======= ===========================

.. _lts_api_0041__response_tag_fields_info:

.. table:: **Table 6** tag_fields_info

   ========== ======= ===========================
   Parameter  Type    Description
   ========== ======= ===========================
   fieldName  String  Field name.
   type       String  Field type.
   content    String  Content.
   isAnalysis Boolean Whether parsing is enabled.
   index      Integer Field sequence number.
   ========== ======= ===========================

.. _lts_api_0041__response_showstructtemplaterule:

.. table:: **Table 7** ShowStructTemplateRule

   ========= ====== ======================
   Parameter Type   Description
   ========= ====== ======================
   param     String Structuring parameter.
   type      String Structuring type.
   ========= ====== ======================

.. _lts_api_0041__response_showstructtemplateclusterinfo:

.. table:: **Table 8** ShowStructTemplateclusterInfo

   +-------------------------+---------+------------------------------------------------------------+
   | Parameter               | Type    | Description                                                |
   +=========================+=========+============================================================+
   | cluster_name            | String  | Kafka cluster name.                                        |
   +-------------------------+---------+------------------------------------------------------------+
   | kafka_bootstrap_servers | String  | Kafka cluster server address.                              |
   +-------------------------+---------+------------------------------------------------------------+
   | kafka_ssl_enable        | Boolean | Whether SSL encrypted authentication is enabled for Kafka. |
   +-------------------------+---------+------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 9** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 401**

.. table:: **Table 10** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 11** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 12** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

.. code-block:: text

   GET https://{endpoint}/v2/{project_id}/lts/struct/template?logGroupId=123456&logStreamId=654321

Example Responses
-----------------

**Status code: 200**

Details of the structuring rule are returned.

.. code-block::

   {
     "demoFields" : [ {
       "content" : "100.19.10.178",
       "fieldName" : "authority",
       "index" : 0,
       "isAnalysis" : true,
       "type" : "string"
     }, {
       "content" : "0",
       "fieldName" : "bytes_received",
       "index" : 0,
       "isAnalysis" : true,
       "type" : "string"
     }, {
       "content" : "1127",
       "fieldName" : "bytes_sent",
       "index" : 0,
       "isAnalysis" : true,
       "type" : "string"
     } ]
   }

**Status code: 400**

BadRequest. The request is invalid. Modify the request based on the description in **error_msg** before a retry.

.. code-block::

   {
     "errorCode" : "SVCSTG.ALS.200201",
     "errorMessage" : "Query Param is error."
   }

**Status code: 401**

AuthFailed. Authentication failed. Check the token and try again.

.. code-block::

   {
     "error_code" : "LTS.0414",
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
     "error_code" : "LTS.0102",
     "error_msg" : "Query empty."
   }

Status Codes
------------

+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Status Code                       | Description                                                                                                                                                                                  |
+===================================+==============================================================================================================================================================================================+
| 200                               | Details of the structuring rule are returned.                                                                                                                                                |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 400                               | BadRequest. The request is invalid. Modify the request based on the description in **error_msg** before a retry.                                                                             |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 401                               | AuthFailed. Authentication failed. Check the token and try again.                                                                                                                            |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 403                               | Forbidden.The request has been rejected.The server has received the request and understood it, but refuses to respond to it. The client should not repeat the request without modifications. |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 500                               | InternalServerError.                                                                                                                                                                         |
|                                   |                                                                                                                                                                                              |
|                                   | The server has received the request but encountered an internal error.                                                                                                                       |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 503                               | ServiceUnavailable. The requested service is unavailable.                                                                                                                                    |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
