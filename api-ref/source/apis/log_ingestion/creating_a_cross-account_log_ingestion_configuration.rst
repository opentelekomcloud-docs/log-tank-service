:original_name: CreateAgencyAccess.html

.. _CreateAgencyAccess:

Creating a Cross-Account Log Ingestion Configuration
====================================================

Function
--------

This API is used to create a cross-account log ingestion configuration.

URI
---

POST /v2.0/{project_id}/lts/createAgencyAccess

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                |
   +=================+=================+=================+============================================================================================================================================================+
   | project_id      | Yes             | String          | Project ID. For details about how to obtain a project ID, see :ref:`Obtaining the Project ID, Account ID, Log Group ID, and Log Stream ID <lts_api_0006>`. |
   |                 |                 |                 |                                                                                                                                                            |
   |                 |                 |                 | Minimum: **1**                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                            |
   |                 |                 |                 | Maximum: **64**                                                                                                                                            |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                   |
   +=================+=================+=================+===============================================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token obtained from IAM. For details about how to obtain a user token, see :ref:`Obtaining a User Token <lts_api_0004>`. |
   |                 |                 |                 |                                                                                                                               |
   |                 |                 |                 | Minimum: **1**                                                                                                                |
   |                 |                 |                 |                                                                                                                               |
   |                 |                 |                 | Maximum: **10000**                                                                                                            |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type    | Yes             | String          | Set this parameter to **application/json;charset=utf8**.                                                                      |
   |                 |                 |                 |                                                                                                                               |
   |                 |                 |                 | Minimum: **30**                                                                                                               |
   |                 |                 |                 |                                                                                                                               |
   |                 |                 |                 | Maximum: **30**                                                                                                               |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +---------------------+-----------+-------------------------------------------------------------------------------------------------------------------+----------------------------+
   | Parameter           | Mandatory | Type                                                                                                              | Description                |
   +=====================+===========+===================================================================================================================+============================+
   | preview_agency_list | Yes       | Array of :ref:`PreviewAgencyLogAccessReqBody <createagencyaccess__request_previewagencylogaccessreqbody>` objects | Preview of the proxy list. |
   +---------------------+-----------+-------------------------------------------------------------------------------------------------------------------+----------------------------+

.. _createagencyaccess__request_previewagencylogaccessreqbody:

.. table:: **Table 4** PreviewAgencyLogAccessReqBody

   +-------------------------+-----------+--------+-------------------------------------------------+
   | Parameter               | Mandatory | Type   | Description                                     |
   +=========================+===========+========+=================================================+
   | agency_access_type      | Yes       | String | Log ingestion type.                             |
   +-------------------------+-----------+--------+-------------------------------------------------+
   | agency_log_access       | Yes       | String | Cross-account log ingestion configuration name. |
   +-------------------------+-----------+--------+-------------------------------------------------+
   | log_agencyStream_name   | Yes       | String | Delegator log stream name.                      |
   +-------------------------+-----------+--------+-------------------------------------------------+
   | log_agencyStream_id     | Yes       | String | Delegator log stream ID.                        |
   +-------------------------+-----------+--------+-------------------------------------------------+
   | log_agencyGroup_name    | Yes       | String | Delegator log group name.                       |
   +-------------------------+-----------+--------+-------------------------------------------------+
   | log_agencyGroup_id      | Yes       | String | Delegator log group ID.                         |
   +-------------------------+-----------+--------+-------------------------------------------------+
   | log_beAgencystream_name | Yes       | String | Delegatee log stream name.                      |
   +-------------------------+-----------+--------+-------------------------------------------------+
   | log_beAgencystream_id   | Yes       | String | Delegatee log stream ID.                        |
   +-------------------------+-----------+--------+-------------------------------------------------+
   | log_beAgencygroup_name  | Yes       | String | Delegatee log group name.                       |
   +-------------------------+-----------+--------+-------------------------------------------------+
   | log_beAgencygroup_id    | Yes       | String | Delegatee log group ID.                         |
   +-------------------------+-----------+--------+-------------------------------------------------+
   | be_agency_project_id    | Yes       | String | Delegatee project ID.                           |
   +-------------------------+-----------+--------+-------------------------------------------------+
   | agency_project_id       | Yes       | String | Delegator project ID.                           |
   +-------------------------+-----------+--------+-------------------------------------------------+
   | agency_domain_name      | Yes       | String | Delegator account name.                         |
   +-------------------------+-----------+--------+-------------------------------------------------+
   | agency_name             | Yes       | String | Agency name.                                    |
   +-------------------------+-----------+--------+-------------------------------------------------+

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 5** Response body parameters

   +-------------------------------+------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------+
   | Parameter                     | Type                                                                                                             | Description                                                               |
   +===============================+==================================================================================================================+===========================================================================+
   | LTSAgencyAccessConfigInfoList | Array of :ref:`LTSAccessConfigInfoRespon200 <createagencyaccess__response_ltsaccessconfiginforespon200>` objects | Response list for creating a log ingestion configuration across accounts. |
   +-------------------------------+------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------+

.. _createagencyaccess__response_ltsaccessconfiginforespon200:

.. table:: **Table 6** LTSAccessConfigInfoRespon200

   +--------------------+----------------------------------------------------------------------------------------------------------+-----------------------------------------+
   | Parameter          | Type                                                                                                     | Description                             |
   +====================+==========================================================================================================+=========================================+
   | access_config_id   | String                                                                                                   | Cross-account log ingestion ID.         |
   +--------------------+----------------------------------------------------------------------------------------------------------+-----------------------------------------+
   | project_id         | String                                                                                                   | Project ID.                             |
   +--------------------+----------------------------------------------------------------------------------------------------------+-----------------------------------------+
   | access_config_name | String                                                                                                   | Cross-account log ingestion name.       |
   +--------------------+----------------------------------------------------------------------------------------------------------+-----------------------------------------+
   | access_config_type | Object                                                                                                   | Cross-account log ingestion type.       |
   +--------------------+----------------------------------------------------------------------------------------------------------+-----------------------------------------+
   | group_id           | String                                                                                                   | Log group ID.                           |
   +--------------------+----------------------------------------------------------------------------------------------------------+-----------------------------------------+
   | log_group_name     | String                                                                                                   | Log group name.                         |
   +--------------------+----------------------------------------------------------------------------------------------------------+-----------------------------------------+
   | log_stream_id      | String                                                                                                   | Log stream ID.                          |
   +--------------------+----------------------------------------------------------------------------------------------------------+-----------------------------------------+
   | log_stream_name    | String                                                                                                   | Log stream name.                        |
   +--------------------+----------------------------------------------------------------------------------------------------------+-----------------------------------------+
   | create_time        | Long                                                                                                     | Creation time.                          |
   +--------------------+----------------------------------------------------------------------------------------------------------+-----------------------------------------+
   | agency_log_access  | :ref:`PreviewAgencyLogAccessReqBody <createagencyaccess__response_previewagencylogaccessreqbody>` object | Information of the delegated ingestion. |
   +--------------------+----------------------------------------------------------------------------------------------------------+-----------------------------------------+

.. _createagencyaccess__response_previewagencylogaccessreqbody:

.. table:: **Table 7** PreviewAgencyLogAccessReqBody

   +-------------------------+--------+-------------------------------------------------+
   | Parameter               | Type   | Description                                     |
   +=========================+========+=================================================+
   | agency_access_type      | String | Log ingestion type.                             |
   +-------------------------+--------+-------------------------------------------------+
   | agency_log_access       | String | Cross-account log ingestion configuration name. |
   +-------------------------+--------+-------------------------------------------------+
   | log_agencyStream_name   | String | Delegator log stream name.                      |
   +-------------------------+--------+-------------------------------------------------+
   | log_agencyStream_id     | String | Delegator log stream ID.                        |
   +-------------------------+--------+-------------------------------------------------+
   | log_agencyGroup_name    | String | Delegator log group name.                       |
   +-------------------------+--------+-------------------------------------------------+
   | log_agencyGroup_id      | String | Delegator log group ID.                         |
   +-------------------------+--------+-------------------------------------------------+
   | log_beAgencystream_name | String | Delegatee log stream name.                      |
   +-------------------------+--------+-------------------------------------------------+
   | log_beAgencystream_id   | String | Delegatee log stream ID.                        |
   +-------------------------+--------+-------------------------------------------------+
   | log_beAgencygroup_name  | String | Delegatee log group name.                       |
   +-------------------------+--------+-------------------------------------------------+
   | log_beAgencygroup_id    | String | Delegatee log group ID.                         |
   +-------------------------+--------+-------------------------------------------------+
   | be_agency_project_id    | String | Delegatee project ID.                           |
   +-------------------------+--------+-------------------------------------------------+
   | agency_project_id       | String | Delegator project ID.                           |
   +-------------------------+--------+-------------------------------------------------+
   | agency_domain_name      | String | Delegator account name.                         |
   +-------------------------+--------+-------------------------------------------------+
   | agency_name             | String | Agency name.                                    |
   +-------------------------+--------+-------------------------------------------------+

**Status code: 400**

.. table:: **Table 8** Response body parameters

   +-----------+--------------------------------------------------------------------------------+---------------------+
   | Parameter | Type                                                                           | Description         |
   +===========+================================================================================+=====================+
   | message   | :ref:`ErrorMessagebody <createagencyaccess__response_errormessagebody>` object | Error message body. |
   +-----------+--------------------------------------------------------------------------------+---------------------+

.. _createagencyaccess__response_errormessagebody:

.. table:: **Table 9** ErrorMessagebody

   ========= ====== ==============
   Parameter Type   Description
   ========= ====== ==============
   code      String Error code.
   details   String Error message.
   ========= ====== ==============

**Status code: 500**

.. table:: **Table 10** Response body parameters

   +-----------+----------------------------------------------------------------------------------+---------------------+
   | Parameter | Type                                                                             | Description         |
   +===========+==================================================================================+=====================+
   | message   | :ref:`ErrorMessagebody <createagencyaccess__response_errormessagebody_1>` object | Error message body. |
   +-----------+----------------------------------------------------------------------------------+---------------------+

.. _createagencyaccess__response_errormessagebody_1:

.. table:: **Table 11** ErrorMessagebody

   ========= ====== ==============
   Parameter Type   Description
   ========= ====== ==============
   code      String Error code.
   details   String Error message.
   ========= ====== ==============

Example Requests
----------------

Creating a cross-account log ingestion configuration

.. code-block:: text

   POST https://{endpoint}/v2.0/{project_id}/lts/createAgencyAccess

   {
     "preview_agency_list" : [ {
       "agency_log_access" : "rule_lb30",
       "agency_access_type" : "AGENCYACCESS",
       "agency_name" : "wenshufeng",
       "agency_domain_name" : "paas_aom_z00418070_01",
       "agency_project_id" : "a0a12b069ab4491185d7cf26c3e86ada",
       "be_agency_project_id" : "2a473356cca5487f8373be891bffc1cf",
       "log_agencyStream_name" : "lts-topic-bug",
       "log_agencyStream_id" : "beb169ff-e6e9-4bea-8e77-50afdec74071",
       "log_agencyGroup_name" : "lts-group-sgq",
       "log_agencyGroup_id" : "f06cbfa0-7243-4031-9380-ae0465bd3997",
       "log_beAgencystream_name" : "lts-topic-ECS",
       "log_beAgencystream_id" : "36ce06b0-c6bf-436d-9abe-39de86da28bb",
       "log_beAgencygroup_name" : "lts-group-sgqECS",
       "log_beAgencygroup_id" : "1e749063-d9f5-474f-a537-00cad4e9a108"
     } ]
   }

Example Responses
-----------------

**Status code: 201**

The cross-account log ingestion configuration is created.

.. code-block::

   [ {
     "access_config_id" : "e929f40e-d1cf-4d59-b656-a2995cbd3229",
     "access_config_name" : "rule_lb30",
     "access_config_type" : "AGENCYACCESS",
     "agency_log_access" : {
       "agency_accessConfig_id" : "e929f40e-d1cf-4d59-b656-a2995cbd3229",
       "agency_access_type" : "AGENCYACCESS",
       "agency_domain_name" : "paas_aom_z00418070_01",
       "agency_log_access" : "rule_lb30",
       "agency_name" : "wenshufeng",
       "agency_project_id" : "a0a12b069ab4491185d7cf26c3e86ada",
       "be_agency_project_id" : "2a473356cca5487f8373be891bffc1cf",
       "log_agencyGroup_id" : "f06cbfa0-7243-4031-9380-ae0465bd3997",
       "log_agencyGroup_name" : "lts-group-sgq",
       "log_agencyStream_id" : "beb169ff-e6e9-4bea-8e77-50afdec74071",
       "log_agencyStream_name" : "lts-topic-bug",
       "log_beAgencygroup_id" : "1e749063-d9f5-474f-a537-00cad4e9a108",
       "log_beAgencygroup_name" : "lts-group-sgqECS",
       "log_beAgencystream_id" : "36ce06b0-c6bf-436d-9abe-39de86da28bb",
       "log_beAgencystream_name" : "lts-topic-ECS"
     },
     "binary_collect" : false,
     "create_time" : 1694400753168,
     "group_id" : "1e749063-d9f5-474f-a537-00cad4e9a108",
     "hostGroupNum" : 0,
     "hostNum" : 0,
     "host_group_info_list" : [ ],
     "host_rule_info" : {
       "black_paths" : [ ],
       "pathType" : "host_file",
       "paths" : [ ],
       "stderr" : false,
       "stdout" : false
     },
     "id" : "",
     "indexId" : "",
     "key" : "",
     "log_group_name" : "lts-group-sgqECS",
     "log_split" : false,
     "log_stream_id" : "36ce06b0-c6bf-436d-9abe-39de86da28bb",
     "log_stream_name" : "lts-topic-ECS",
     "pathNum" : 0,
     "project_id" : "2a473356cca5487f8373be891bffc1cf",
     "tag_list" : [ ]
   } ]

**Status code: 400**

Failed to create cross-account log ingestion configuration.

.. code-block::

   {
     "message" : {
       "code" : "LTS.0420",
       "details" : "Agency not existed, check domain name and agency name"
     }
   }

**Status code: 500**

Internal service error

.. code-block::

   {
     "message" : {
       "code" : "LTS.0010",
       "details" : "The system encountered an internal error"
     }
   }

Status Codes
------------

=========== ===========================================================
Status Code Description
=========== ===========================================================
201         The cross-account log ingestion configuration is created.
400         Failed to create cross-account log ingestion configuration.
500         Internal service error
=========== ===========================================================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
