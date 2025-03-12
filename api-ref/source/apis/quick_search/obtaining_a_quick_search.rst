:original_name: ListCriterias.html

.. _ListCriterias:

Obtaining a Quick Search
========================

Function
--------

This API is used to obtain quick search.

URI
---

GET /v1.0/{project_id}/groups/{group_id}/topics/{topic_id}/search-criterias

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

.. table:: **Table 2** Query Parameters

   =========== ========= ====== ===========
   Parameter   Mandatory Type   Description
   =========== ========= ====== ===========
   search_type No        String Raw logs.
   =========== ========= ====== ===========

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
   | Content-Type    | Yes             | String          | Set this parameter to **application/json;charset=UTF-8**.                                                                     |
   |                 |                 |                 |                                                                                                                               |
   |                 |                 |                 | Minimum: **30**                                                                                                               |
   |                 |                 |                 |                                                                                                                               |
   |                 |                 |                 | Maximum: **30**                                                                                                               |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +------------------+-----------------------------------------------------------------------------------------------------------+----------------+
   | Parameter        | Type                                                                                                      | Description    |
   +==================+===========================================================================================================+================+
   | search_criterias | Array of :ref:`GetQuerySearchCriteriasBody <listcriterias__response_getquerysearchcriteriasbody>` objects | Response body. |
   +------------------+-----------------------------------------------------------------------------------------------------------+----------------+

.. _listcriterias__response_getquerysearchcriteriasbody:

.. table:: **Table 5** GetQuerySearchCriteriasBody

   =========== ====== ========================
   Parameter   Type   Description
   =========== ====== ========================
   criteria    String Quick search of a field.
   name        String Quick search of a name.
   id          String Quick search ID.
   search_type String Quick search type.
   =========== ====== ========================

**Status code: 400**

.. table:: **Table 6** Response body parameters

   +-----------+---------------------------------------------------------------------------+---------------------+
   | Parameter | Type                                                                      | Description         |
   +===========+===========================================================================+=====================+
   | message   | :ref:`ErrorMessagebody <listcriterias__response_errormessagebody>` object | Error message body. |
   +-----------+---------------------------------------------------------------------------+---------------------+

.. _listcriterias__response_errormessagebody:

.. table:: **Table 7** ErrorMessagebody

   ========= ====== ==============
   Parameter Type   Description
   ========= ====== ==============
   code      String Error code.
   details   String Error message.
   ========= ====== ==============

**Status code: 500**

.. table:: **Table 8** Response body parameters

   +-----------+-----------------------------------------------------------------------------+---------------------+
   | Parameter | Type                                                                        | Description         |
   +===========+=============================================================================+=====================+
   | message   | :ref:`ErrorMessagebody <listcriterias__response_errormessagebody_1>` object | Error message body. |
   +-----------+-----------------------------------------------------------------------------+---------------------+

.. _listcriterias__response_errormessagebody_1:

.. table:: **Table 9** ErrorMessagebody

   ========= ====== ==============
   Parameter Type   Description
   ========= ====== ==============
   code      String Error code.
   details   String Error message.
   ========= ====== ==============

Example Requests
----------------

Obtaining a Quick Search

.. code-block:: text

   GET /v1.0/2a473356cca5487f8373be891bffc1cf/groups/d1f4240d-5ee2-4e0b-9e2c-e25c7978c001/topics/2b899d46-218c-4f0c-8ace-a36a290a83a0/search-criterias?search_type=ORIGINALLOG

Example Responses
-----------------

**Status code: 200**

Quick search obtained.

.. code-block::

   {
     "search_criterias" : [ {
       "criteria" : "content : 1234567891234567891234567891234567891234567891234567891234567894",
       "name" : "Creating a Number",
       "id" : "0eb379f5-f847-4d25-ba89-05967bf1bae3",
       "search_type" : "ORIGINALLOG"
     } ]
   }

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
     "error_code" : "LTS.0203",
     "error_msg" : "Internal Server Error"
   }

Status Codes
------------

+-------------+-----------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                   |
+=============+===============================================================================================+
| 200         | Quick search obtained.                                                                        |
+-------------+-----------------------------------------------------------------------------------------------+
| 400         | Invalid request. Modify the request based on the description in **error_msg** before a retry. |
+-------------+-----------------------------------------------------------------------------------------------+
| 500         | The server has received the request but encountered an internal error.                        |
+-------------+-----------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
