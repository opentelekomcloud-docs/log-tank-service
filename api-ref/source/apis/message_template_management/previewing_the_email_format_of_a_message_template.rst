:original_name: ListNotificationTemplate.html

.. _ListNotificationTemplate:

Previewing the Email Format of a Message Template
=================================================

Function
--------

This API is used to preview the email format of a notification template.

URI
---

POST /v2/{project_id}/{domain_id}/lts/events/notification/templates/view

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

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                            |
   +=================+=================+=================+========================================================================================+
   | templates       | Yes             | String          | Email template content.                                                                |
   |                 |                 |                 |                                                                                        |
   |                 |                 |                 | Minimum: **2**                                                                         |
   |                 |                 |                 |                                                                                        |
   |                 |                 |                 | Maximum: **1024**                                                                      |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------+
   | language        | Yes             | String          | Language type, for example, **en-us**.                                                 |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------+
   | source          | Yes             | String          | Source. The value can only be LTS.                                                     |
   |                 |                 |                 |                                                                                        |
   |                 |                 |                 | Minimum: **3**                                                                         |
   |                 |                 |                 |                                                                                        |
   |                 |                 |                 | Maximum: **3**                                                                         |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------+
   | subject         | No              | String          | The content of this field is rendered to be used as the title of the message template. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+--------+------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                          |
   +===========+========+======================================================================================================+
   | template  | String | The value is an HTML text and needs to be parsed before being displayed.                             |
   +-----------+--------+------------------------------------------------------------------------------------------------------+
   | subject   | String | The title displayed after the field is parsed. It is displayed at the top of the returned HTML text. |
   +-----------+--------+------------------------------------------------------------------------------------------------------+

**Status code: 500**

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Previewing the email format of a message template

.. code-block:: text

   POST https://{endpoint}/v2/{project_id}/{domain_id}/lts/events/notification/templates/view

   {
     "templates" : "Severity: ${event_severity};\nOccurred: ${starts_at};\nAlarm source: $event.metadata.resource_provider;\nResource type: $event.metadata.resource_type;\nResource ID: ${resources};\nStatistical type: by keyword;\nExpression: $event.annotations.condition_expression;\nCurrent value: $event.annotations.current_value;\nStatistical period: $event.annotations.frequency;\nQuery time: $event.annotations.results[0].time;\nQuery log: $event.annotations.results[0].raw_results;",
     "language" : "en-us",
     "source" : "LTS",
     "subject" : "${region_name}[${event_severity}_${event_type}_${clear_type}] generated an alarm at ${starts_at}"
   }

Example Responses
-----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
     "template" : "<style>    span {        display: inline-block;        float: left;        font-size: 14px;    }    b {        display: inline-block;        float: left;        color: #252B3A;        font-size: 14px    }</style><table border=\"0\" cellpadding=\"0\" cellspacing=\"0\"       style=\"font-family:Helvetica,Arial,PingFangSC-Regular,Hiragino Sans GB;border-spacing:0px 14px;font-size:14px;padding-left: 30px;line-height:25px;\">    <thead>    <tr style=\"font-size:14px;\">        <td colspan=\"2\" style=\"line-height:28px;color:#6e6e6e;font-size:14px\">            <b>Dear&nbsp;</b>            <b>user,</b>            <b>&nbsp;, </b>        </td>    </tr>    </thead>    <tr>        <td colspan=\"2\">            <span>One notification has been&nbsp;</span>            <span>added</span>            <span>&nbsp;in region&nbsp;</span>            <b>xx</b>            <span>&nbsp;based on&nbsp;</span>            <span>alarm rule&nbsp;</span>            <b>action_rule</b>            <span>. For more information, go to the LTS console.</span>            <br>            <br>        </td>    </tr>    <tr style=\"font-size:14px;\">        <td colspan=\"2\">            <p style=\"margin-top: -26px;margin-bottom: -20px;\">            <br>                <span style=\"color:#252B3A;line-height:24px\">Here are the details.</span>            </p>        </td>    </tr>    <td><div>Severity: Major;<br>Occurred: 2022-03-21 18:23:20 GMT+08:00;<br>Alarm source: N/A;<br>Resource type: N/A;<br>Resource ID: CCE;<br>Statistical type: by keyword;<br>Expression: N/A;<br>Current value: N/A;<br>Statistical period: N/A;<br>Query time: N/A;<br>Query log: N/A;<br><div/></td>  </table>",
     "subject" : "[Major_alarm_add] generated an alarm at 2022-03-21 18:23:20 GMT+08:00",
       }
   }

**Status code: 500**

An error is reported when an incorrect domain ID is entered.

.. code-block::

   {
     "error_code" : "LTS.2019",
     "error_msg" : "Failed to preview notification template."
   }

Status Codes
------------

=========== ============================================================
Status Code Description
=========== ============================================================
200         The request is successful.
500         An error is reported when an incorrect domain ID is entered.
=========== ============================================================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
