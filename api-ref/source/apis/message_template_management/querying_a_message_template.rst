:original_name: ShowNotificationTemplate.html

.. _ShowNotificationTemplate:

Querying a Message Template
===========================

Function
--------

This API is used to query a notification template.

URI
---

GET /v2/{project_id}/{domain_id}/lts/events/notification/template/{template_name}

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
   | template_name   | Yes             | String          | template_name                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | Minimum: **1**                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | Maximum: **100**                                                                                                                                            |
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

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-------------+----------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Type                                                                                               | Description                                                                                                                                                |
   +=============+====================================================================================================+============================================================================================================================================================+
   | name        | String                                                                                             | Notification rule name.                                                                                                                                    |
   +-------------+----------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type        | Array of strings                                                                                   | Notification method.                                                                                                                                       |
   +-------------+----------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | desc        | String                                                                                             | Template description.                                                                                                                                      |
   +-------------+----------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | source      | String                                                                                             | Template source.                                                                                                                                           |
   +-------------+----------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | locale      | String                                                                                             | Language.                                                                                                                                                  |
   +-------------+----------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | templates   | Array of :ref:`SubTemplateResBody <shownotificationtemplate__response_subtemplateresbody>` objects | Template body, which is an array.                                                                                                                          |
   +-------------+----------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time | Long                                                                                               | Creation time (timestamp in milliseconds).                                                                                                                 |
   +-------------+----------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | modify_time | Long                                                                                               | Update time (timestamp in milliseconds).                                                                                                                   |
   +-------------+----------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id  | String                                                                                             | Project ID. For details about how to obtain a project ID, see :ref:`Obtaining the Account ID, Project ID, Log Group ID, and Log Stream ID <lts_api_0006>`. |
   +-------------+----------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _shownotificationtemplate__response_subtemplateresbody:

.. table:: **Table 4** SubTemplateResBody

   +-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                                                                     |
   +===========+========+=================================================================================================================================================================================+
   | sub_type  | String | Template subtype, for example, **sms** or **email**.                                                                                                                            |
   +-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | content   | String | Sub-template body. A variable following a dollar symbol ($) can only be one of the following variables. The supported variables vary according to alarm types (keyword or SQL). |
   +-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | topic     | String | Email subject. This parameter is valid only when **sub_type** is set to **email**.                                                                                              |
   +-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

**Status code: 401**

.. table:: **Table 5** Response body parameters

   +-----------+------------------------------------------------------------------------------------------+----------------+
   | Parameter | Type                                                                                     | Description    |
   +===========+==========================================================================================+================+
   | message   | :ref:`CodeDetailsRspBody <shownotificationtemplate__response_codedetailsrspbody>` object | Error message. |
   +-----------+------------------------------------------------------------------------------------------+----------------+

.. _shownotificationtemplate__response_codedetailsrspbody:

.. table:: **Table 6** CodeDetailsRspBody

   ========= ====== ==============
   Parameter Type   Description
   ========= ====== ==============
   code      String Error code.
   details   String Error message.
   ========= ====== ==============

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

Querying a message template with a specified name

.. code-block:: text

   GET https://{endpoint}/v2/{project_id}/{domain_id}/lts/events/notification/template/{template_name}

   /v2/{project_id}/{domain_id}/lts/events/notification/template/{template_name}

Example Responses
-----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
     "create_time" : 1702955600631,
     "desc" : "description",
     "locale" : "en-us",
     "modify_time" : 1702955600631,
     "name" : "postman-test",
     "project_id" : "2a473356cca5487f8373be891bffc1cf",
     "source" : "LTS",
     "templates" : [ {
       "content" : "Severity: ${event_severity};\nOccurred: ${starts_at};\nResource ID: ${resources};\nStatistical type: by keyword;\nExpression: $event.annotations.condition_expression;\nCurrent value: $event.annotations.current_value;\nStatistical period: $event.annotations.frequency;",
       "sub_type" : "sms"
     }, {
       "content" : "Severity: ${event_severity};\nOccurred: ${starts_at};\nAlarm source: $event.metadata.resource_provider;\nResource type: $event.metadata.resource_type;\nResource ID: ${resources};\nStatistical type: by keyword;\nExpression: $event.annotations.condition_expression;\nCurrent value: $event.annotations.current_value;\nStatistical period: $event.annotations.frequency;\nQuery time: $event.annotations.results[0].time;\nQuery log: $event.annotations.results[0].raw_results;",
       "sub_type" : "email"
     } ],
     "type" : [ ]
   }

**Status code: 401**

ID verification failed.

.. code-block::

   {
     "message" : {
       "code" : "LTS.0001",
       "details" : "project verify error"
     }
   }

**Status code: 500**

The server has received the request but encountered an internal error.

.. code-block::

   {
     "error_code" : "LTS.2018",
     "error_msg" : "Failed to get notification template."
   }

Status Codes
------------

+-------------+------------------------------------------------------------------------+
| Status Code | Description                                                            |
+=============+========================================================================+
| 200         | The request is successful.                                             |
+-------------+------------------------------------------------------------------------+
| 401         | ID verification failed.                                                |
+-------------+------------------------------------------------------------------------+
| 500         | The server has received the request but encountered an internal error. |
+-------------+------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
