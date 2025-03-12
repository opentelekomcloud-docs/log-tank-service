:original_name: CreateNotificationTemplate.html

.. _CreateNotificationTemplate:

Creating a Message Template
===========================

Function
--------

This API is used to create a notification template. Currently, each account can create a maximum of 100 notification templates. After a notification template is created, its name cannot be changed.

URI
---

POST /v2/{project_id}/{domain_id}/lts/events/notification/templates

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                 |
   +=================+=================+=================+=============================================================================================================================================================+
   | project_id      | Yes             | String          | Project ID. For details about how to obtain a project ID, see :ref:`Obtaining the Project ID, Account ID, Log Group ID, and Log Stream ID <lts_api_0006>`.  |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | Minimum: **32**                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | Maximum: **32**                                                                                                                                             |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | domain_id       | Yes             | String          | Account ID. For details about how to obtain an account ID, see :ref:`Obtaining the Project ID, Account ID, Log Group ID, and Log Stream ID <lts_api_0006>`. |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | Minimum: **32**                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | Maximum: **32**                                                                                                                                             |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   +-----------------+-----------------+---------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                                  | Description                                                                                                                                                                                                                                                                         |
   +=================+=================+=======================================================================================+=====================================================================================================================================================================================================================================================================================+
   | name            | Yes             | String                                                                                | Notification rule name, which is mandatory. The value can contain only digits, letters, underscores (_), and hyphens (-), and cannot start or end with special characters such as underscores. The value can contain 1 to 100 characters and cannot be changed after being created. |
   |                 |                 |                                                                                       |                                                                                                                                                                                                                                                                                     |
   |                 |                 |                                                                                       | Minimum: **1**                                                                                                                                                                                                                                                                      |
   |                 |                 |                                                                                       |                                                                                                                                                                                                                                                                                     |
   |                 |                 |                                                                                       | Maximum: **100**                                                                                                                                                                                                                                                                    |
   +-----------------+-----------------+---------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type            | No              | Array of strings                                                                      | Notification method.                                                                                                                                                                                                                                                                |
   +-----------------+-----------------+---------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | desc            | No              | String                                                                                | Template description, which is mandatory. The value can contain only digits, letters, and underscores (_), and cannot start or end with an underscore. The value can contain 0 to 1,024 characters.                                                                                 |
   |                 |                 |                                                                                       |                                                                                                                                                                                                                                                                                     |
   |                 |                 |                                                                                       | Minimum: **0**                                                                                                                                                                                                                                                                      |
   |                 |                 |                                                                                       |                                                                                                                                                                                                                                                                                     |
   |                 |                 |                                                                                       | Maximum: **1024**                                                                                                                                                                                                                                                                   |
   +-----------------+-----------------+---------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | source          | Yes             | String                                                                                | Template source. Currently, this parameter must be set to LTS. Otherwise, the template cannot be filtered.                                                                                                                                                                          |
   |                 |                 |                                                                                       |                                                                                                                                                                                                                                                                                     |
   |                 |                 |                                                                                       | Minimum: **3**                                                                                                                                                                                                                                                                      |
   |                 |                 |                                                                                       |                                                                                                                                                                                                                                                                                     |
   |                 |                 |                                                                                       | Maximum: **3**                                                                                                                                                                                                                                                                      |
   +-----------------+-----------------+---------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | locale          | Yes             | String                                                                                | Language type, for example, **en-us**.                                                                                                                                                                                                                                              |
   +-----------------+-----------------+---------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | templates       | Yes             | Array of :ref:`SubTemplate <createnotificationtemplate__request_subtemplate>` objects | Template body is an array.                                                                                                                                                                                                                                                          |
   +-----------------+-----------------+---------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _createnotificationtemplate__request_subtemplate:

.. table:: **Table 4** SubTemplate

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                          |
   +=================+=================+=================+======================================================================================================================================================================================================================================+
   | sub_type        | Yes             | String          | Template subtype, for example, **sms** or **email**.                                                                                                                                                                                 |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | content         | Yes             | String          | Sub-template body. A variable following a dollar symbol ($) can only be one of the following variables. The supported variables vary according to alarm types. Currently, the variables supported for keyword alarms are as follows: |
   |                 |                 |                 |                                                                                                                                                                                                                                      |
   |                 |                 |                 | -  Severity: ${event_severity};                                                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                                      |
   |                 |                 |                 | -  Occurred: ${starts_at};                                                                                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                                                                                                      |
   |                 |                 |                 | -  Alarm source: $event.metadata.resource_provider;                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                                      |
   |                 |                 |                 | -  Resource type: $event.metadata.resource_type;                                                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                                      |
   |                 |                 |                 | -  Resource ID: ${resources};                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                                      |
   |                 |                 |                 | -  Statistical type: by keyword;                                                                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                                      |
   |                 |                 |                 | -  Expression: $event.annotations.condition_expression;                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                                      |
   |                 |                 |                 | -  Current value: $event.annotations.current_value;                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                                      |
   |                 |                 |                 | -  Statistical period: $event.annotations.frequency;                                                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                                                                      |
   |                 |                 |                 | -  Query time: $event.annotations.results[0].time;                                                                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                                                                      |
   |                 |                 |                 | -  Query log: $event.annotations.results[0].raw_results;                                                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                                                                      |
   |                 |                 |                 | .. note::                                                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                                      |
   |                 |                 |                 |    Each variable must be followed by an English semicolon (;). Otherwise, the template replacement fails.                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                                      |
   |                 |                 |                 | Minimum: **2**                                                                                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                                                                      |
   |                 |                 |                 | Maximum: **1024**                                                                                                                                                                                                                    |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | topic           | No              | String          | Email subject. This parameter is valid only when **sub_type** is set to **email**.                                                                                                                                                   |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   +-----------+------------------------------------------------------------------------------------------------------+-----------------------------------+
   | Parameter | Type                                                                                                 | Description                       |
   +===========+======================================================================================================+===================================+
   | name      | String                                                                                               | Notification rule name.           |
   +-----------+------------------------------------------------------------------------------------------------------+-----------------------------------+
   | type      | Array of strings                                                                                     | Notification method.              |
   +-----------+------------------------------------------------------------------------------------------------------+-----------------------------------+
   | desc      | String                                                                                               | Template description.             |
   +-----------+------------------------------------------------------------------------------------------------------+-----------------------------------+
   | source    | String                                                                                               | Template source.                  |
   +-----------+------------------------------------------------------------------------------------------------------+-----------------------------------+
   | locale    | String                                                                                               | Language.                         |
   +-----------+------------------------------------------------------------------------------------------------------+-----------------------------------+
   | templates | Array of :ref:`SubTemplateResBody <createnotificationtemplate__response_subtemplateresbody>` objects | Template body, which is an array. |
   +-----------+------------------------------------------------------------------------------------------------------+-----------------------------------+

.. _createnotificationtemplate__response_subtemplateresbody:

.. table:: **Table 6** SubTemplateResBody

   +-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                                                                     |
   +===========+========+=================================================================================================================================================================================+
   | sub_type  | String | Template subtype, for example, **sms** or **email**.                                                                                                                            |
   +-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | content   | String | Sub-template body. A variable following a dollar symbol ($) can only be one of the following variables. The supported variables vary according to alarm types (keyword or SQL). |
   +-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | topic     | String | Email subject. This parameter is valid only when **sub_type** is set to **email**.                                                                                              |
   +-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

Creating a message template

.. code-block:: text

   POST https://{endpoint}/v2/{project_id}/{domain_id}/lts/events/notification/templates

   {
     "name" : "alarm-template",
     "desc" : "test",
     "source" : "LTS",
     "locale" : "en-us",
     "templates" : [ {
       "sub_type" : "sms",
       "content" : "Severity: ${event_severity};\nOccurred: ${starts_at};\nResource ID: ${resources};\nStatistical type: by keyword;\nExpression: $event.annotations.condition_expression;\nCurrent value: $event.annotations.current_value;\nStatistical period: $event.annotations.frequency;"
     }, {
       "sub_type" : "email",
       "content" : "Severity: ${event_severity};\nOccurred: ${starts_at};\nAlarm source: $event.metadata.resource_provider;\nResource type: $event.metadata.resource_type;\nResource ID: ${resources};\nStatistical type: by keyword;\nExpression: $event.annotations.condition_expression;\nCurrent value: $event.annotations.current_value;\nStatistical period: $event.annotations.frequency;\nQuery time: $event.annotations.results[0].time;\nQuery log: $event.annotations.results[0].raw_results;"
     } ]
   }

Example Responses
-----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
     "desc" : "description",
     "locale" : "en-us",
     "name" : "postman-test",
     "source" : "LTS",
     "templates" : [ {
       "content" : "Severity: ${event_severity};\nOccurred: ${starts_at};\nResource ID: ${resources};\nStatistical type: by keyword;\nExpression: $event.annotations.condition_expression;\nCurrent value: $event.annotations.current_value;\nStatistical period: $event.annotations.frequency;",
       "sub_type" : "sms"
     }, {
       "content" : "Severity: ${event_severity};\nOccurred: ${starts_at};\nAlarm source: $event.metadata.resource_provider;\nResource type: $event.metadata.resource_type;\nResource ID: ${resources};\nStatistical type: by keyword;\nExpression: $event.annotations.condition_expression;\nCurrent value: $event.annotations.current_value;\nStatistical period: $event.annotations.frequency;\nQuery time: $event.annotations.results[0].time;\nQuery log: $event.annotations.results[0].raw_results;",
       "sub_type" : "email"
     } ]
   }

**Status code: 400**

Invalid request. Modify the request based on the description in **error_msg** before a retry.

.. code-block::

   {
     "error_code" : "LTS.2014",
     "error_msg" : "desc is invalid!"
   }

**Status code: 500**

The server has received the request but encountered an internal error.

.. code-block::

   {
     "error_code" : "LTS.2014",
     "error_msg" : "Failed to create notification template."
   }

Status Codes
------------

+-------------+-----------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                   |
+=============+===============================================================================================+
| 200         | The request is successful.                                                                    |
+-------------+-----------------------------------------------------------------------------------------------+
| 400         | Invalid request. Modify the request based on the description in **error_msg** before a retry. |
+-------------+-----------------------------------------------------------------------------------------------+
| 500         | The server has received the request but encountered an internal error.                        |
+-------------+-----------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
