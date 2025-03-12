:original_name: lts_api_0092.html

.. _lts_api_0092:

Deleting an Active Alarm
========================

Function
--------

This API is used to delete an active alarm.

URI
---

POST /v2/{project_id}/{domain_id}/lts/alarms/sql-alarm/clear

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

   +-----------+-----------+-------------------------------------------------------------+--------------------+
   | Parameter | Mandatory | Type                                                        | Description        |
   +===========+===========+=============================================================+====================+
   | events    | Yes       | Array of :ref:`Event <lts_api_0092__request_event>` objects | Topic information. |
   +-----------+-----------+-------------------------------------------------------------+--------------------+

.. _lts_api_0092__request_event:

.. table:: **Table 4** Event

   +-----------------+-----------------+---------------------------------------------------------+------------------------------------+
   | Parameter       | Mandatory       | Type                                                    | Description                        |
   +=================+=================+=========================================================+====================================+
   | metadata        | Yes             | :ref:`Metadata <lts_api_0092__request_metadata>` object | Alarm information.                 |
   |                 |                 |                                                         |                                    |
   |                 |                 |                                                         | Minimum length: 0                  |
   |                 |                 |                                                         |                                    |
   |                 |                 |                                                         | Maximum length: 2048               |
   +-----------------+-----------------+---------------------------------------------------------+------------------------------------+
   | starts_at       | Yes             | Long                                                    | Alarm generation time (timestamp). |
   |                 |                 |                                                         |                                    |
   |                 |                 |                                                         | Minimum: **0**                     |
   |                 |                 |                                                         |                                    |
   |                 |                 |                                                         | Maximum: **32**                    |
   +-----------------+-----------------+---------------------------------------------------------+------------------------------------+

.. _lts_api_0092__request_metadata:

.. table:: **Table 5** Metadata

   ================= ========= ====== ==============================
   Parameter         Mandatory Type   Description
   ================= ========= ====== ==============================
   event_type        Yes       String Alarm type.
   event_id          Yes       String Alarm ID.
   event_severity    Yes       String Alarm severity.
   event_name        Yes       String Alarm name.
   resource_type     Yes       String Resource type.
   resource_id       Yes       String Log group/stream name.
   resource_provider Yes       String Alarm source.
   lts_alarm_type    Yes       String Alarm rule type (SQL/keyword).
   ================= ========= ====== ==============================

Response Parameters
-------------------

None

Example Requests
----------------

Deleting an active alarm by alarm ID

.. code-block:: text

   POST https://{endpoint}/v2/{project_id}/{domain_id}/lts/alarms/sql-alarm/clear

   {
     "events" : [ {
       "metadata" : {
         "event_type" : "alarm",
         "event_id" : "1",
         "lts_alarm_type" : "keywords/sql",
         "resource_type" : "Log group/stream.",
         "event_severity" : "Critical",
         "resource_id" : "lts-group-demo/lts-topic-demo",
         "event_name" : "demo",
         "resource_provider" : "LTS"
       },
       "starts_at" : 1629947408497
     } ]
   }

Example Responses
-----------------

None

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
