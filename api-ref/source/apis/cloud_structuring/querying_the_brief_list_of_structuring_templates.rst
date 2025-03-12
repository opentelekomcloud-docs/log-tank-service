:original_name: ListBreifStructTemplate.html

.. _ListBreifStructTemplate:

Querying the Brief List of Structuring Templates
================================================

Function
--------

This API is used to query the brief list of structuring templates.

URI
---

GET /v3/{project_id}/lts/struct/customtemplate/list

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

   +-----------+---------------------------------------------------------------------------------------------------------------+--------------------------------------+
   | Parameter | Type                                                                                                          | Description                          |
   +===========+===============================================================================================================+======================================+
   | results   | Array of :ref:`BriefStructTemplateModel <listbreifstructtemplate__response_briefstructtemplatemodel>` objects | Brief list of structuring templates. |
   +-----------+---------------------------------------------------------------------------------------------------------------+--------------------------------------+

.. _listbreifstructtemplate__response_briefstructtemplatemodel:

.. table:: **Table 4** BriefStructTemplateModel

   +---------------+--------+---------------------------------------------------------------------------------------------+
   | Parameter     | Type   | Description                                                                                 |
   +===============+========+=============================================================================================+
   | create_time   | Long   | Template creation/update time.                                                              |
   +---------------+--------+---------------------------------------------------------------------------------------------+
   | id            | String | Template ID.                                                                                |
   +---------------+--------+---------------------------------------------------------------------------------------------+
   | template_name | String | Template name.                                                                              |
   +---------------+--------+---------------------------------------------------------------------------------------------+
   | template_type | String | Structuring type. Currently, regular expression, JSON, delimiters, and Nginx are supported. |
   +---------------+--------+---------------------------------------------------------------------------------------------+
   | project_id    | String | Project ID.                                                                                 |
   +---------------+--------+---------------------------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 5** Response body parameters

   +-----------+---------------------------------------------------------------------------------------------------+------------------------+
   | Parameter | Type                                                                                              | Description            |
   +===========+===================================================================================================+========================+
   | message   | :ref:`CustomTemplateErrorCode <listbreifstructtemplate__response_customtemplateerrorcode>` object | Request error message. |
   +-----------+---------------------------------------------------------------------------------------------------+------------------------+

.. _listbreifstructtemplate__response_customtemplateerrorcode:

.. table:: **Table 6** CustomTemplateErrorCode

   ========= ====== ===============
   Parameter Type   Description
   ========= ====== ===============
   code      String LTS error code.
   details   String Error message.
   ========= ====== ===============

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

Obtaining the Brief List of Structuring Templates of the Current Tenant

.. code-block:: text

   GET https://{endpoint}/v3/{project_id}/lts/struct/customtemplate/list

   /v3/{project_id}/lts/struct/customtemplate/list

Example Responses
-----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
     "results" : [ {
       "create_time" : 1632897983441,
       "id" : "47629e46-287d-478c-8888-xxxxxxxxxxxx",
       "template_name" : "jsonTemplate",
       "template_type" : "json",
       "project_id" : "2a473356cca5487f8373be89xxxxxxxx"
     } ]
   }

**Status code: 400**

Custom log template operation failed.

.. code-block::

   {
     "message" : {
       "code" : "LTS.0757",
       "details" : "Log custom template operation failed"
     }
   }

**Status code: 500**

The server has received the request but encountered an internal error.

.. code-block::

   {
     "error_code" : "LTS.2017",
     "error_msg" : "Find struct template failed."
   }

Status Codes
------------

+-------------+------------------------------------------------------------------------+
| Status Code | Description                                                            |
+=============+========================================================================+
| 200         | The request is successful.                                             |
+-------------+------------------------------------------------------------------------+
| 400         | Custom log template operation failed.                                  |
+-------------+------------------------------------------------------------------------+
| 500         | The server has received the request but encountered an internal error. |
+-------------+------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
