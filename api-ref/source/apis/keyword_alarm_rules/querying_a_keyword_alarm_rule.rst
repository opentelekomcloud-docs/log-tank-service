:original_name: lts_api_0083.html

.. _lts_api_0083:

Querying a Keyword Alarm Rule
=============================

Function
--------

This API is used to query a keyword alarm.

URI
---

GET /v2/{project_id}/lts/alarms/keywords-alarm-rule

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

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +----------------------+------------------------------------------------------------------------------------------------------+-------------+
   | Parameter            | Type                                                                                                 | Description |
   +======================+======================================================================================================+=============+
   | keywords_alarm_rules | Array of :ref:`KeywordsAlarmRuleRespList <lts_api_0083__response_keywordsalarmruleresplist>` objects | Project ID. |
   +----------------------+------------------------------------------------------------------------------------------------------+-------------+

.. _lts_api_0083__response_keywordsalarmruleresplist:

.. table:: **Table 4** KeywordsAlarmRuleRespList

   +---------------------------------+----------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                       | Type                                                                             | Description                                                                                                                                                   |
   +=================================+==================================================================================+===============================================================================================================================================================+
   | projectId                       | String                                                                           | Project ID.                                                                                                                                                   |
   +---------------------------------+----------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | keywords_alarm_rule_id          | String                                                                           | Keyword alarm ID.                                                                                                                                             |
   +---------------------------------+----------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | keywords_alarm_rule_name        | String                                                                           | Keyword alarm rule name.                                                                                                                                      |
   +---------------------------------+----------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | keywords_alarm_rule_description | String                                                                           | Keyword alarm description.                                                                                                                                    |
   +---------------------------------+----------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | condition_expression            | String                                                                           | Condition.                                                                                                                                                    |
   +---------------------------------+----------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | keywords_requests               | Array of :ref:`KeywordsRequest <lts_api_0083__response_keywordsrequest>` objects | Keyword details.                                                                                                                                              |
   +---------------------------------+----------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | frequency                       | :ref:`Frequency <lts_api_0083__response_frequency>` object                       | Alarm statistical period.                                                                                                                                     |
   +---------------------------------+----------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | keywords_alarm_level            | String                                                                           | Alarm severity.                                                                                                                                               |
   +---------------------------------+----------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | keywords_alarm_send             | Boolean                                                                          | Whether to send an alarm.                                                                                                                                     |
   +---------------------------------+----------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | domain_id                       | String                                                                           | Domain ID                                                                                                                                                     |
   +---------------------------------+----------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time                     | Long                                                                             | Creation time (timestamp in milliseconds).                                                                                                                    |
   +---------------------------------+----------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | update_time                     | Long                                                                             | Update time (timestamp in milliseconds).                                                                                                                      |
   +---------------------------------+----------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | topics                          | Array of :ref:`Topics <lts_api_0083__response_topics>` objects                   | Notification topic, which will be unavailable soon. You are advised to use the action rule function.                                                          |
   +---------------------------------+----------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | template_name                   | String                                                                           | Message template name.                                                                                                                                        |
   +---------------------------------+----------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                          | String                                                                           | Alarm status.                                                                                                                                                 |
   +---------------------------------+----------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | trigger_condition_count         | Integer                                                                          | Number of queries in which the triggering condition is met. The default value is **1**.                                                                       |
   +---------------------------------+----------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | trigger_condition_frequency     | Integer                                                                          | Number of times that log events meet the trigger condition. The default value is **1**.                                                                       |
   +---------------------------------+----------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | whether_recovery_policy         | Boolean                                                                          | Whether to enable the alarm clearance notification. The default value is **false**.                                                                           |
   +---------------------------------+----------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | recovery_policy                 | Integer                                                                          | Number of queries in which the triggering condition is not met. The alarm is cleared when this number reaches the value (**3** by default) of this parameter. |
   +---------------------------------+----------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | notification_frequency          | Integer                                                                          | Notification frequency, in minutes.                                                                                                                           |
   +---------------------------------+----------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | alarm_action_rule_name          | String                                                                           | Alarm action rule name.                                                                                                                                       |
   +---------------------------------+----------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                              | String                                                                           | The value is the same as that of **keywords_alarm_rule_id**.                                                                                                  |
   +---------------------------------+----------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | indexId                         | String                                                                           | The value is the same as that of **keywords_alarm_rule_id**.                                                                                                  |
   +---------------------------------+----------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | key                             | String                                                                           | The value is the same as that of **keywords_alarm_rule_id**.                                                                                                  |
   +---------------------------------+----------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _lts_api_0083__response_keywordsrequest:

.. table:: **Table 5** KeywordsRequest

   +------------------------+---------+---------------------------------------------------------------------------------------------------------------------------------+
   | Parameter              | Type    | Description                                                                                                                     |
   +========================+=========+=================================================================================================================================+
   | log_stream_id          | String  | Log stream ID.                                                                                                                  |
   +------------------------+---------+---------------------------------------------------------------------------------------------------------------------------------+
   | log_stream_name        | String  | Log stream name.                                                                                                                |
   +------------------------+---------+---------------------------------------------------------------------------------------------------------------------------------+
   | log_group_id           | String  | Log group ID.                                                                                                                   |
   +------------------------+---------+---------------------------------------------------------------------------------------------------------------------------------+
   | log_group_name         | String  | Log group name.                                                                                                                 |
   +------------------------+---------+---------------------------------------------------------------------------------------------------------------------------------+
   | keywords               | String  | Keyword.                                                                                                                        |
   +------------------------+---------+---------------------------------------------------------------------------------------------------------------------------------+
   | condition              | String  | Condition.                                                                                                                      |
   +------------------------+---------+---------------------------------------------------------------------------------------------------------------------------------+
   | number                 | Integer | Keyword threshold, which forms a condition with **keyword** and **condition**. An alarm is triggered when the condition is met. |
   +------------------------+---------+---------------------------------------------------------------------------------------------------------------------------------+
   | search_time_range      | Integer | Time range for querying the latest data when a task is executed.                                                                |
   +------------------------+---------+---------------------------------------------------------------------------------------------------------------------------------+
   | search_time_range_unit | String  | Query time unit.                                                                                                                |
   +------------------------+---------+---------------------------------------------------------------------------------------------------------------------------------+

.. _lts_api_0083__response_frequency:

.. table:: **Table 6** Frequency

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                             |
   +=======================+=======================+=========================================================================================================================================================================================================================+
   | type                  | String                | Time type.                                                                                                                                                                                                              |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cron_expr             | String                | Cron expression, which uses the 24-hour format and is precise down to the minute.                                                                                                                                       |
   |                       |                       |                                                                                                                                                                                                                         |
   |                       |                       | • 0/10 \* \* \* \*: The query starts from 00:00 and is performed every 10 minutes at 00:00, 00:10, 00:20, 00:30, 00:40, 00:50, 01:00, and so on. For example, if the current time is 16:37, the next query is at 16:50. |
   |                       |                       |                                                                                                                                                                                                                         |
   |                       |                       | • 0 0/5 \* \* \*: The query starts from 00:00 and is performed every 5 hours at 00:00, 05:00, 10:00, 15:00, 20:00, and so on. For example, if the current time is 16:37, the next query is at 20:00.                    |
   |                       |                       |                                                                                                                                                                                                                         |
   |                       |                       | • 0 14 \* \* \*: The query is performed at 14:00 every day.                                                                                                                                                             |
   |                       |                       |                                                                                                                                                                                                                         |
   |                       |                       | • 0 0 10 \* \*: The query is performed at 00:00 on the 10th day of every month.                                                                                                                                         |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | hour_of_day           | Integer               | This field is used when **type** is set to **DAILY** or **WEEKLY**.                                                                                                                                                     |
   |                       |                       |                                                                                                                                                                                                                         |
   |                       |                       | **DAILY** ranges from 0 to 23.                                                                                                                                                                                          |
   |                       |                       |                                                                                                                                                                                                                         |
   |                       |                       | **WEEKLY** ranges from 0 to 23.                                                                                                                                                                                         |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | day_of_week           | Integer               | This field is used when **type** is set to **WEEKLY** (from Sunday to Saturday).                                                                                                                                        |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | fixed_rate            | Integer               | Value of a period. This field is used when **type** is set to **FIXED_RATE**. It is used together with **fixed_rate_unit** to indicate a fixed period.                                                                  |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | fixed_rate_unit       | String                | Unit of a period. This field is used when **type** is set to **FIXED_RATE**. It is used together with **fixed_rate** to indicate a fixed period.                                                                        |
   |                       |                       |                                                                                                                                                                                                                         |
   |                       |                       | The value can be **hour** or **minute**.                                                                                                                                                                                |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _lts_api_0083__response_topics:

.. table:: **Table 7** Topics

   +--------------+---------+---------------------------------------------------------------------------------------------------------+
   | Parameter    | Type    | Description                                                                                             |
   +==============+=========+=========================================================================================================+
   | name         | String  | Topic name.                                                                                             |
   +--------------+---------+---------------------------------------------------------------------------------------------------------+
   | topic_urn    | String  | Specifies the resource identifier of the topic, which is unique.                                        |
   +--------------+---------+---------------------------------------------------------------------------------------------------------+
   | display_name | String  | Specifies the topic display name, which is presented as the name of the email sender in email messages. |
   +--------------+---------+---------------------------------------------------------------------------------------------------------+
   | push_policy  | Integer | Specifies the message push policy.                                                                      |
   +--------------+---------+---------------------------------------------------------------------------------------------------------+

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

Querying a keyword alarm rule

.. code-block:: text

   GET https://{endpoint}/v2/{project_id}/lts/alarms/keywords-alarm-rule

   /v2/{project_id}/lts/alarms/keywords-alarm-rule

Example Responses
-----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
     "keywords_alarm_rules" : [ {
       "alarm_action_rule_name" : "Alarm Action Rule Name",
       "alarm_rule_alias" : "APITest",
       "condition_expressions" : [ {
         "alarm_level" : "CRITICAL",
         "condition_expression" : "Matching Log Events>1"
       } ],
       "create_time" : 1736498043489,
       "domain_id" : "78ac2cb7c0be4d0482bd7d949830e0b8",
       "frequency" : {
         "cron_expr" : "",
         "day_of_week" : 1,
         "fixed_rate" : 1,
         "fixed_rate_unit" : "minute",
         "hour_of_day" : 0,
         "type" : "FIXED_RATE"
       },
       "keywords_alarm_level" : "CRITICAL",
       "id" : "025a5375-c548-498c-8330-219cf8a1dbbf",
       "indexId" : "025a5375-c548-498c-8330-219cf8a1dbbf",
       "key" : "025a5375-c548-498c-8330-219cf8a1dbbf",
       "keywords_alarm_rule_description" : "",
       "keywords_alarm_rule_id" : "025a5375-c548-498c-8330-219cf8a1dbbf",
       "keywords_alarm_rule_name" : "APITest",
       "keywords_alarm_send" : true,
       "keywords_requests" : [ {
         "condition" : ">",
         "conditions" : [ {
           "alarm_level" : "CRITICAL",
           "condition" : ">",
           "number" : 1
         } ],
         "eps_id" : "0",
         "is_time_range_relative" : true,
         "keywords" : "aaa",
         "log_group_id" : "b2ead43b-c055-4581-8c13-56af52b6bc13",
         "log_group_name" : "lts-group-mwb002",
         "log_group_name_alias" : "lts-group-mwb002",
         "log_stream_id" : "072795c7-ce92-4ea3-b359-1928d47ab152",
         "log_stream_name" : "lts-topic-coredns",
         "log_stream_name_alias" : "lts-topic-coredns",
         "number" : 1,
         "search_time_range" : 5,
         "search_time_range_unit" : "minute"
       } ],
       "language" : "zh-cn",
       "notification_frequency" : 0,
       "projectId" : "a0a12b069ab4491185d7cf26c3e86ada",
       "query_version" : "v2",
       "query_version_for_query" : "newVersion",
       "recovery_policy" : 3,
       "status" : "RUNNING",
       "tags" : [ {
         "key" : "tagTest",
         "value" : "level"
       } ],
       "topics" : [ ],
       "trigger_condition_count" : 1,
       "trigger_condition_frequency" : 1,
       "update_time" : 1736498043489,
       "whether_recovery_policy" : true
     }, {
       "projectId" : "string",
       "keywords_alarm_rule_id" : "string",
       "keywords_alarm_rule_name" : "string",
       "keywords_alarm_rule_description" : "string",
       "condition_expression" : "string",
       "keywords_requests" : [ {
         "log_stream_id" : "string",
         "log_stream_name" : "string",
         "log_group_id" : "string",
         "log_group_name" : "string",
         "keywords" : "string",
         "condition" : ">=",
         "number" : 1,
         "search_time_range" : 0,
         "search_time_range_unit" : "minute"
       } ],
       "frequency" : {
         "type" : "CRON",
         "cron_expr" : "string",
         "hour_of_day" : 0,
         "day_of_week" : 0,
         "fixed_rate" : 0,
         "fixed_rate_unit" : "minute"
       },
       "keywords_alarm_level" : "Info",
       "keywords_alarm_send" : true,
       "domain_id" : "string",
       "create_time" : 0,
       "update_time" : 0,
       "template_name" : "Message template name.",
       "status" : "RUNNING",
       "trigger_condition_count" : "1",
       "trigger_condition_frequency" : "1",
       "whether_recovery_policy" : false,
       "recovery_policy" : "3",
       "notification_frequency" : 5,
       "alarm_action_rule_name" : "",
       "topics" : [ {
         "name" : "string",
         "topic_urn" : "string",
         "display_name" : "test-smn",
         "push_policy" : 0
       } ]
     } ]
   }

**Status code: 500**

The server has received the request but encountered an internal error.

.. code-block::

   {
     "error_code" : "LTS.2008",
     "error_msg" : "Find Alarm rule failed."
   }

Status Codes
------------

+-------------+------------------------------------------------------------------------+
| Status Code | Description                                                            |
+=============+========================================================================+
| 200         | The request is successful.                                             |
+-------------+------------------------------------------------------------------------+
| 500         | The server has received the request but encountered an internal error. |
+-------------+------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
