:original_name: lts_api_0084.html

.. _lts_api_0084:

Deleting a Keyword Alarm Rule
=============================

Function
--------

This API is used to delete a keyword alarm.

URI
---

DELETE /v2/{project_id}/lts/alarms/keywords-alarm-rule/{keywords_alarm_rule_id}

.. table:: **Table 1** Path Parameters

   +------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter              | Mandatory       | Type            | Description                                                                                                                                                |
   +========================+=================+=================+============================================================================================================================================================+
   | project_id             | Yes             | String          | Project ID. For details about how to obtain a project ID, see :ref:`Obtaining the Project ID, Account ID, Log Group ID, and Log Stream ID <lts_api_0006>`. |
   |                        |                 |                 |                                                                                                                                                            |
   |                        |                 |                 | Minimum: **32**                                                                                                                                            |
   |                        |                 |                 |                                                                                                                                                            |
   |                        |                 |                 | Maximum: **32**                                                                                                                                            |
   +------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | keywords_alarm_rule_id | Yes             | String          | Keyword alarm rule ID.                                                                                                                                     |
   |                        |                 |                 |                                                                                                                                                            |
   |                        |                 |                 | Minimum: **36**                                                                                                                                            |
   |                        |                 |                 |                                                                                                                                                            |
   |                        |                 |                 | Maximum: **36**                                                                                                                                            |
   +------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

**Status code: 400**

.. table:: **Table 3** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 4** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Deleting a keyword alarm by alarm ID

.. code-block:: text

   DELETE https://{endpoint}/v2/{project_id}/lts/alarms/keywords-alarm-rule/{keywords_alarm_rule_id}

   /v2/{project_id}/lts/alarms/keywords-alarm-rule/{keywords_alarm_rule_id}

Example Responses
-----------------

**Status code: 200**

The request is successful.

.. code-block::

   None

**Status code: 400**

Error response content.

.. code-block::

   {
     "error_code" : "LTS.2007",
     "error_msg" : "Alarm rule not exist."
   }

**Status code: 500**

The server has received the request but encountered an internal error.

.. code-block::

   {
     "error_code" : "LTS.2002",
     "error_msg" : "Failed to update alarm rule."
   }

Status Codes
------------

+-------------+------------------------------------------------------------------------+
| Status Code | Description                                                            |
+=============+========================================================================+
| 200         | The request is successful.                                             |
+-------------+------------------------------------------------------------------------+
| 400         | Error response content.                                                |
+-------------+------------------------------------------------------------------------+
| 500         | The server has received the request but encountered an internal error. |
+-------------+------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
