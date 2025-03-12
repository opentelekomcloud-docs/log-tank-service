:original_name: ListStructTemplate.html

.. _ListStructTemplate:

Querying a Structuring Template
===============================

Function
--------

This API is used to query a structuring template.

Note:

A user can call this API for up to 50 times per second.

URI
---

GET /v3/{project_id}/lts/struct/customtemplate

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

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                          |
   +=================+=================+=================+======================================================================================================================================================================+
   | id              | No              | String          | ID of the template to be queried. This parameter is optional. If this parameter is not specified, all custom structuring templates used in the project are returned. |
   |                 |                 |                 |                                                                                                                                                                      |
   |                 |                 |                 | Minimum: **36**                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                      |
   |                 |                 |                 | Maximum: **36**                                                                                                                                                      |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   +-----------+------------------------------------------------------------------------------------------------+----------------------------------------------------+
   | Parameter | Type                                                                                           | Description                                        |
   +===========+================================================================================================+====================================================+
   | results   | Array of :ref:`StructTemplateModel <liststructtemplate__response_structtemplatemodel>` objects | Array of queried customized structuring templates. |
   +-----------+------------------------------------------------------------------------------------------------+----------------------------------------------------+

.. _liststructtemplate__response_structtemplatemodel:

.. table:: **Table 5** StructTemplateModel

   +---------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------+
   | Parameter     | Type                                                                           | Description                                                                    |
   +===============+================================================================================+================================================================================+
   | project_id    | String                                                                         | Project ID.                                                                    |
   +---------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------+
   | template_name | String                                                                         | Template name.                                                                 |
   +---------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------+
   | template_type | String                                                                         | Template type. The options are regular expression, JSON, delimiter, and Nginx. |
   +---------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------+
   | demo_log      | String                                                                         | Sample log event.                                                              |
   +---------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------+
   | demo_fields   | Array of :ref:`DemoField <liststructtemplate__response_demofield>` objects     | Example field array.                                                           |
   +---------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------+
   | tag_fields    | Array of :ref:`TagFieldNew <liststructtemplate__response_tagfieldnew>` objects | Tag field array.                                                               |
   +---------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------+
   | rule          | :ref:`TemplateRule <liststructtemplate__response_templaterule>` object         | Structuring rule object.                                                       |
   +---------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------+
   | demo_label    | String                                                                         | Example log tag.                                                               |
   +---------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------+
   | create_time   | Long                                                                           | Creation time.                                                                 |
   +---------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------+
   | id            | String                                                                         | Template ID.                                                                   |
   +---------------+--------------------------------------------------------------------------------+--------------------------------------------------------------------------------+

.. _liststructtemplate__response_demofield:

.. table:: **Table 6** DemoField

   +-----------------------+-----------------------+------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                        |
   +=======================+=======================+====================================================================================+
   | field_name            | String                | Field name.                                                                        |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------+
   | content               | String                | Example field content, which is the example value of a field.                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------+
   | type                  | String                | Field data type.                                                                   |
   |                       |                       |                                                                                    |
   |                       |                       | Value: **string**, **long**, or **float**                                          |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------+
   | is_analysis           | Boolean               | Whether to enable quick analysis.                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------+
   | index                 | Integer               | Field number in manual regular expression and delimiter modes.                     |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------+
   | relation              | String                | Describes the hierarchical relationship between fields in a multi-level JSON file. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------+
   | user_defined_name     | String                | Custom field alias in JSON and Nginx modes.                                        |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------+

.. _liststructtemplate__response_tagfieldnew:

.. table:: **Table 7** TagFieldNew

   +-----------------------+-----------------------+---------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                   |
   +=======================+=======================+===============================================================+
   | field_name            | String                | Field name.                                                   |
   +-----------------------+-----------------------+---------------------------------------------------------------+
   | content               | String                | Example field content, which is the example value of a field. |
   +-----------------------+-----------------------+---------------------------------------------------------------+
   | type                  | String                | Field data type.                                              |
   |                       |                       |                                                               |
   |                       |                       | Value: **string**, **long**, or **float**                     |
   +-----------------------+-----------------------+---------------------------------------------------------------+
   | is_analysis           | Boolean               | Whether to enable quick analysis.                             |
   +-----------------------+-----------------------+---------------------------------------------------------------+
   | index                 | Integer               | Sequence number (starting from 0).                            |
   +-----------------------+-----------------------+---------------------------------------------------------------+

.. _liststructtemplate__response_templaterule:

.. table:: **Table 8** TemplateRule

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
   +=======================+=======================+======================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+
   | type                  | String                | Structuring type. Currently, regular expression, JSON, delimiters, and Nginx are supported.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | param                 | String                | Specific structuring rule. Each structuring type has a unique structure:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                       |                       | A manual regular expression is a JSON string that contains the **keyObject** and **regex_rules** objects. **keyObject** contains key-value pairs, where a key indicates the index of an element in the **demo_fields** array, and a value indicates **field_name**. **regex_rules** is a regular expression. Example:                                                                                                                                                                                                                                                                |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                       |                       | .. code-block::                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                       |                       |    {\"keyObject\":{\"1\":\"date\",\"2\":\"num\"},\"regex_rules\":\"^(?<date>[^/]+)(?:[^]* ){8}(?<num>\\\\d+)\"}                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                       |                       | In JSON mode, **param** is a JSON string that contains the **keyObject** and **layers** objects. **keyObject** contains key-value pairs, where a key indicates the **field_name** of an element in the **demo_fields** array, and a value indicates **user_defined_name**. **layers** indicates the maximum number of parsing layers. Its maximum value is 4. Example:                                                                                                                                                                                                               |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                       |                       | .. code-block::                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                       |                       |    {\"keyObject\":{\"metadata.dimension\":\"dimension\",\"metadata.value\":\"\",\"metadata.unit\":\"\",\"collectionTime\":\"\"},\"layers\":3}                                                                                                                                                                                                                                                                                                                                                                                                                                        |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                       |                       | The delimiter mode uses a JSON string that contains the **keyObject** and **tokenizer** objects. **keyObject** contains key-value pairs, where a key indicates the index of an element in the **demo_fields** array, and a value indicates **field_name**. **tokenizer** indicates delimiters. Example:                                                                                                                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                       |                       | .. code-block::                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                       |                       |    {\"keyObject\":{\"0\":\"field1\",\"1\":\"field2\",\"2\":\"field3\",\"3\":\"field4\",\"4\":\"field5\",\"5\":\"field6\",\"6\":\"field7\",\"7\":\"field8\",\"8\":\"field9\"},\"tokenizer\":\"\"}                                                                                                                                                                                                                                                                                                                                                                                     |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                       |                       | The Nginx mode uses a JSON string that contains the **keyObject**, **regex**, **field_names**, and **log_format** objects. **keyObject** contains key-value pairs, where a key indicates the **field_name** of an element in the **demo_fields** array, and a value indicates **user_defined_name**. **regex** is a regular expression, where the **field_names** object is the combination of **field_name** of each element in the **demo_fields** array. **field_names** are separated by commas (,). The **log_format** object indicates the Nginx log formatting mode. Example: |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                       |                       | .. code-block::                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                       |                       |    {\"keyObject\": {        \"http_host\": \"host\",        \"remote_addr\": \"\",          \"request_method\": \"\",       \"request_uri\": \"\",          \"time_local\": \"\"    },      \"regex\": \"(\\\\d+/\\\\S+/\\\\d+:\\\\d+:\\\\d+:\\\\d+)\\\\s+\\\\S+\\\\s+(\\\\S*)\\\\s+(\\\\S*)\\\\s+(\\\\S*)\\\\s+\\\"([^\\\"]*)\\\".*\",     \"fieldNames\": \"time_local,remote_addr,request_method,http_host,request_uri\",    \"log_format\": \"log_format '$upstreaminfo '$time_local $remote_addr  $request_method $http_host\\\"$request_uri\\\"';\" }                          |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 9** Response body parameters

   +-----------+----------------------------------------------------------------------------------------------+------------------------+
   | Parameter | Type                                                                                         | Description            |
   +===========+==============================================================================================+========================+
   | message   | :ref:`CustomTemplateErrorCode <liststructtemplate__response_customtemplateerrorcode>` object | Request error message. |
   +-----------+----------------------------------------------------------------------------------------------+------------------------+

.. _liststructtemplate__response_customtemplateerrorcode:

.. table:: **Table 10** CustomTemplateErrorCode

   ========= ====== ===============
   Parameter Type   Description
   ========= ====== ===============
   code      String LTS error code.
   details   String Error message.
   ========= ====== ===============

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

Querying Details About the Current Structuring Template

.. code-block:: text

   GET https://{endpoint}/v3/{project_id}/lts/struct/customtemplate?id=bc8e3f2c-87fe-4acd-8439-69cdf29251c1

   /v3/{project_id}/lts/struct/customtemplate?id=bc8e3f2c-87fe-4acd-8439-69cdf29251c1

Example Responses
-----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
     "results" : [ {
       "create_time" : 1641258099551,
       "demo_fields" : [ {
         "content" : "2022-01-03/14:52:28",
         "field_name" : "field1",
         "index" : 0,
         "is_analysis" : true,
         "type" : "string"
       }, {
         "content" : "this",
         "field_name" : "field2",
         "index" : 1,
         "is_analysis" : true,
         "type" : "string"
       }, {
         "content" : "log",
         "field_name" : "field3",
         "index" : 2,
         "is_analysis" : false,
         "type" : "string"
       }, {
         "content" : "is",
         "field_name" : "field4",
         "index" : 3,
         "is_analysis" : false,
         "type" : "string"
       }, {
         "content" : "Error",
         "field_name" : "field5",
         "index" : 4,
         "is_analysis" : false,
         "type" : "string"
       }, {
         "content" : "NO",
         "field_name" : "field6",
         "index" : 5,
         "is_analysis" : false,
         "type" : "string"
       }, {
         "content" : "13 testing.",
         "field_name" : "field7",
         "index" : 6,
         "is_analysis" : false,
         "type" : "string"
       }, {
         "content" : "286",
         "field_name" : "field8",
         "index" : 7,
         "is_analysis" : false,
         "type" : "long"
       } ],
       "demo_log" : "2022-01-03/14:52:28 this log is Error NO 13 testing 286.",
       "id" : "43a8cc7b-b632-4c36-a65d-8150e98219f1",
       "project_id" : "2a473356cca5487f8373be89xxxxxxxx",
       "rule" : {
         "param" : "{\"keyObject\":{\"0\":\"field1\",\"1\":\"field2\",\"2\":\"field3\",\"3\":\"field4\",\"4\":\"field5\",\"5\":\"field6\",\"6\":\"field7\",\"7\":\"field8\"},\"tokenizer\":\" \"}",
         "type" : "split"
       },
       "demo_label" : "here is a demo label",
       "tag_fields" : [ {
         "content" : "172.16.10.69",
         "field_name" : "hostIP",
         "index" : 0,
         "is_analysis" : true,
         "type" : "string"
       } ],
       "template_name" : "testSplit13",
       "template_type" : "split"
     } ]
   }

**Status code: 400**

The ID does not exist.

.. code-block::

   {
     "message" : {
       "code" : "LTS.0751",
       "details" : "custom template doesn't exist"
     }
   }

**Status code: 500**

The server has received the request but encountered an internal error.

.. code-block::

   {
     "error_code" : "LTS.2017",
     "error_msg" : "Find struct template failed."
   }

Status Codes
------------

+-------------+------------------------------------------------------------------------+
| Status Code | Description                                                            |
+=============+========================================================================+
| 200         | The request is successful.                                             |
+-------------+------------------------------------------------------------------------+
| 400         | The ID does not exist.                                                 |
+-------------+------------------------------------------------------------------------+
| 500         | The server has received the request but encountered an internal error. |
+-------------+------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
