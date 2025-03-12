:original_name: DeleteSearchCriterias.html

.. _DeleteSearchCriterias:

Deleting a Quick Search
=======================

Function
--------

This API is used to delete a quick search.

URI
---

DELETE /v1.0/{project_id}/groups/{group_id}/topics/{topic_id}/search-criterias

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
   | group_id        | Yes             | String          | ID of the log group whose log streams will be queried. Generally, it contains 36 characters.                                                               |
   |                 |                 |                 |                                                                                                                                                            |
   |                 |                 |                 | Minimum: **36**                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                            |
   |                 |                 |                 | Maximum: **36**                                                                                                                                            |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | topic_id        | Yes             | String          | Log stream ID.                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                            |
   |                 |                 |                 | Minimum: **36**                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                            |
   |                 |                 |                 | Maximum: **36**                                                                                                                                            |
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
   | Content-Type    | Yes             | String          | Set this parameter to **application/json;charset=UTF-8**.                                                                     |
   |                 |                 |                 |                                                                                                                               |
   |                 |                 |                 | Minimum: **30**                                                                                                               |
   |                 |                 |                 |                                                                                                                               |
   |                 |                 |                 | Maximum: **30**                                                                                                               |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   ========= ========= ====== ======================
   Parameter Mandatory Type   Description
   ========= ========= ====== ======================
   epsId     No        String Enterprise project ID.
   id        Yes       String Quick search ID.
   ========= ========= ====== ======================

Response Parameters
-------------------

**Status code: 400**

.. table:: **Table 4** Response body parameters

   +-----------+-----------------------------------------------------------------------------------+---------------------+
   | Parameter | Type                                                                              | Description         |
   +===========+===================================================================================+=====================+
   | message   | :ref:`ErrorMessagebody <deletesearchcriterias__response_errormessagebody>` object | Error message body. |
   +-----------+-----------------------------------------------------------------------------------+---------------------+

.. _deletesearchcriterias__response_errormessagebody:

.. table:: **Table 5** ErrorMessagebody

   ========= ====== ==============
   Parameter Type   Description
   ========= ====== ==============
   code      String Error code.
   details   String Error message.
   ========= ====== ==============

**Status code: 500**

.. table:: **Table 6** Response body parameters

   +-----------+-------------------------------------------------------------------------------------+---------------------+
   | Parameter | Type                                                                                | Description         |
   +===========+=====================================================================================+=====================+
   | message   | :ref:`ErrorMessagebody <deletesearchcriterias__response_errormessagebody_1>` object | Error message body. |
   +-----------+-------------------------------------------------------------------------------------+---------------------+

.. _deletesearchcriterias__response_errormessagebody_1:

.. table:: **Table 7** ErrorMessagebody

   ========= ====== ==============
   Parameter Type   Description
   ========= ====== ==============
   code      String Error code.
   details   String Error message.
   ========= ====== ==============

Example Requests
----------------

Deleting a quick search

.. code-block:: text

   DELETE /v1.0/2a473356cca5487f8373be891bffc1cf/groups/d1f4240d-5ee2-4e0b-9e2c-e25c7978c001/topics/2b899d46-218c-4f0c-8ace-a36a290a83a0/search-criterias

   {
     "id" : "345d2276-1ae8-4495-a6ee-bf77c2e5ffb9",
     "epsId" : "0"
   }

Example Responses
-----------------

**Status code: 204**

Quick search deleted.

.. code-block::

    none

**Status code: 400**

Invalid request. Modify the request based on the description in **error_msg** before a retry.

.. code-block::

   {
     "message" : {
       "code" : "LTS.0208",
       "details" : "The log stream does not existed"
     }
   }

**Status code: 500**

The server has received the request but encountered an internal error.

.. code-block::

   {
     "message" : {
       "code" : "LTS.0203",
       "details" : "Internal Server Error"
     }
   }

Status Codes
------------

+-------------+-----------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                   |
+=============+===============================================================================================+
| 204         | Quick search deleted.                                                                         |
+-------------+-----------------------------------------------------------------------------------------------+
| 400         | Invalid request. Modify the request based on the description in **error_msg** before a retry. |
+-------------+-----------------------------------------------------------------------------------------------+
| 500         | The server has received the request but encountered an internal error.                        |
+-------------+-----------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
