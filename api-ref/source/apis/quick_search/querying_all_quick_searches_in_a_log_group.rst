:original_name: ListQueryAllSearchCriterias.html

.. _ListQueryAllSearchCriterias:

Querying All Quick Searches in a Log Group
==========================================

Function
--------

This API is used to query all quick searches in a log group.

URI
---

GET /v1.0/{project_id}/lts/groups/{group_id}/search-criterias

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

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +------------------+-----------------------------------------------------------------------------------------------------------+---------------+
   | Parameter        | Type                                                                                                      | Description   |
   +==================+===========================================================================================================+===============+
   | search_criterias | Array of :ref:`search_criteriasBody <listqueryallsearchcriterias__response_search_criteriasbody>` objects | Quick search. |
   +------------------+-----------------------------------------------------------------------------------------------------------+---------------+

.. _listqueryallsearchcriterias__response_search_criteriasbody:

.. table:: **Table 4** search_criteriasBody

   +-----------------+-------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
   | Parameter       | Type                                                                                                                    | Description                          |
   +=================+=========================================================================================================================+======================================+
   | criterias       | Array of :ref:`GetQuerySearchCriteriasBody <listqueryallsearchcriterias__response_getquerysearchcriteriasbody>` objects | Quick search of a single log stream. |
   +-----------------+-------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
   | log_stream_id   | String                                                                                                                  | Log stream ID.                       |
   +-----------------+-------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
   | log_stream_name | String                                                                                                                  | Log stream name.                     |
   +-----------------+-------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
   | search_type     | String                                                                                                                  | Quick search type.                   |
   +-----------------+-------------------------------------------------------------------------------------------------------------------------+--------------------------------------+

.. _listqueryallsearchcriterias__response_getquerysearchcriteriasbody:

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

   +-----------+-----------------------------------------------------------------------------------------+---------------------+
   | Parameter | Type                                                                                    | Description         |
   +===========+=========================================================================================+=====================+
   | message   | :ref:`ErrorMessagebody <listqueryallsearchcriterias__response_errormessagebody>` object | Error message body. |
   +-----------+-----------------------------------------------------------------------------------------+---------------------+

.. _listqueryallsearchcriterias__response_errormessagebody:

.. table:: **Table 7** ErrorMessagebody

   ========= ====== ==============
   Parameter Type   Description
   ========= ====== ==============
   code      String Error code.
   details   String Error message.
   ========= ====== ==============

**Status code: 500**

.. table:: **Table 8** Response body parameters

   +-----------+-------------------------------------------------------------------------------------------+---------------------+
   | Parameter | Type                                                                                      | Description         |
   +===========+===========================================================================================+=====================+
   | message   | :ref:`ErrorMessagebody <listqueryallsearchcriterias__response_errormessagebody_1>` object | Error message body. |
   +-----------+-------------------------------------------------------------------------------------------+---------------------+

.. _listqueryallsearchcriterias__response_errormessagebody_1:

.. table:: **Table 9** ErrorMessagebody

   ========= ====== ==============
   Parameter Type   Description
   ========= ====== ==============
   code      String Error code.
   details   String Error message.
   ========= ====== ==============

Example Requests
----------------

Querying All Quick Searches in a Log Group

.. code-block:: text

   GET /v1.0/2a473356cca5487f8373be891bffc1cf/lts/groups/d1f4240d-5ee2-4e0b-9e2c-e25c7978c001/search-criterias

Example Responses
-----------------

**Status code: 200**

Obtained.

.. code-block::

   {
     "search_criterias" : [ {
       "criterias" : [ {
         "criteria" : "234",
         "name" : "234",
         "id" : "aee53496-xxxx-xxxx-xxxx-5a83d1aae134",
         "search_type" : "ORIGINALLOG"
       }, {
         "criteria" : "24",
         "name" : "2342",
         "id" : "939c930a-xxxx-xxxx-xxxx-a3040d857ce1",
         "search_type" : "ORIGINALLOG"
       } ],
       "log_stream_id" : "85025a4b-xxxx-xxxx-xxxx-2b6851d84ea2",
       "log_stream_name" : "lts-test-topic",
       "search_type" : "ORIGINALLOG"
     } ]
   }

**Status code: 400**

Invalid request. Modify the request based on the description in **error_msg** before a retry.

.. code-block::

   {
     "message" : {
       "code" : "LTS.0201",
       "details" : "The log group does not existed"
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
| 200         | Obtained.                                                                                     |
+-------------+-----------------------------------------------------------------------------------------------+
| 400         | Invalid request. Modify the request based on the description in **error_msg** before a retry. |
+-------------+-----------------------------------------------------------------------------------------------+
| 500         | The server has received the request but encountered an internal error.                        |
+-------------+-----------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
