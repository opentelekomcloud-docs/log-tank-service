:original_name: lts_api_0061.html

.. _lts_api_0061:

Querying an SMN Topic
=====================

Function
--------

This API is used to query an SMN topic.

URI
---

GET /v2/{project_id}/lts/notifications/topics

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

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                         |
   +=================+=================+=================+=====================================================================================================================================+
   | offset          | Yes             | Integer         | Query cursor. Set the value to 0 in the first query. In subsequent queries, obtain the value from the response to the last request. |
   |                 |                 |                 |                                                                                                                                     |
   |                 |                 |                 | Minimum: **0**                                                                                                                      |
   |                 |                 |                 |                                                                                                                                     |
   |                 |                 |                 | Maximum: **1024**                                                                                                                   |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | Yes             | Integer         | Number of records on each page. The maximum value is 100.                                                                           |
   |                 |                 |                 |                                                                                                                                     |
   |                 |                 |                 | Minimum: **0**                                                                                                                      |
   |                 |                 |                 |                                                                                                                                     |
   |                 |                 |                 | Maximum: **100**                                                                                                                    |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | fuzzy_name      | No              | String          | Specifies the name of the topic to be searched for, which is fuzzy match. startwith is used for the fuzzy match.                    |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+

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

   +-------------+----------------------------------------------------------------+-------------------------+
   | Parameter   | Type                                                           | Description             |
   +=============+================================================================+=========================+
   | request_id  | String                                                         | Unique ID of a request. |
   +-------------+----------------------------------------------------------------+-------------------------+
   | topic_count | Integer                                                        | Number of topics.       |
   +-------------+----------------------------------------------------------------+-------------------------+
   | topics      | Array of :ref:`Topics <lts_api_0061__response_topics>` objects | Topic information.      |
   +-------------+----------------------------------------------------------------+-------------------------+

.. _lts_api_0061__response_topics:

.. table:: **Table 5** Topics

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

Querying an SMN topic

.. code-block:: text

   GET https://{endpoint}/v2/{project_id}/lts/notifications/topics

   /v2/{project_id}/lts/notifications/topics?offset={offset}&limit={limit}

Example Responses
-----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
     "request_id" : "1",
     "topic_count" : 100,
     "topics" : [ {
       "name" : "test",
       "topic_urn" : "urn:smn:xxxx-7:{projectId}:fyy",
       "display_name" : "username",
       "push_policy" : 0
     } ]
   }

**Status code: 400**

Insufficient permissions.

.. code-block::

   {
     "error_code" : "LTS.2009",
     "error_msg" : "User must have SMN service authority."
   }

**Status code: 500**

The request is successful but the service is abnormal.

.. code-block::

   {
     "error_code" : "LTS.0010",
     "error_msg" : "Internal Server Error"
   }

Status Codes
------------

=========== ======================================================
Status Code Description
=========== ======================================================
200         The request is successful.
400         Insufficient permissions.
500         The request is successful but the service is abnormal.
=========== ======================================================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
