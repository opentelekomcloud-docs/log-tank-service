:original_name: lts_02_0003.html

.. _lts_02_0003:

Creating a Log Group
====================

This API is used to create a log group. All API URLs described in this section must be case-sensitive.

Function
--------

This function describes how to create a log group for log storage and query. You can create a maximum of 100 log groups.

URI
---

-  URI format

   POST /v2.0/{project_id}/log-groups

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= ====== ===========
      Parameter  Mandatory Type   Description
      ========== ========= ====== ===========
      project_id Yes       String Project ID
      ========== ========= ====== ===========

Request
-------

-  Request parameters

   .. table:: **Table 2** Parameter description

      +----------------+---------------+-------------+-------------+---------------------------------------------------------------------------------------------------------------------------------+
      | Parameter      | Sub-Parameter | Mandatory   | Type        | Description                                                                                                                     |
      +================+===============+=============+=============+=================================================================================================================================+
      | log_group_name | N/A           | Yes         | String      | Log group name.                                                                                                                 |
      |                |               |             |             |                                                                                                                                 |
      |                |               |             |             | The configuration rules are as follows:                                                                                         |
      |                |               |             |             |                                                                                                                                 |
      |                |               |             |             | -  Must be a string of 1 to 64 characters.                                                                                      |
      |                |               |             |             | -  Only letters, digits, underscores (_), hyphens (-), and periods (.) are allowed. The name cannot start or end with a period. |
      +----------------+---------------+-------------+-------------+---------------------------------------------------------------------------------------------------------------------------------+
      | ttl_in_days    | N/A           | Yes         | Int         | Log expiration time. The value is fixed to 7 days.                                                                              |
      +----------------+---------------+-------------+-------------+---------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block:: text

      POST /v2.0/{project_id}/log-groups
      {
      "log_group_name":"test01",
      "ttl_in_days": 7
      }

Response
--------

-  Response parameters

   .. table:: **Table 3** Parameter description

      ============ ============= ====== ============
      Parameter    Sub-Parameter Type   Description
      ============ ============= ====== ============
      log_group_id N/A           String Log group ID
      ============ ============= ====== ============

-  Example response

   .. code-block::

      {
       "log_group_id":"56b4b31f-3024-11e9-9023-286ed488ce71"
      }

Returned Value
--------------

-  Normal

   201

-  Abnormal

   For details about status code, see :ref:`Status Code <lts_02_0020>`.
