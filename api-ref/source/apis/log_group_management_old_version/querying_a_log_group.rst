:original_name: lts_02_0004.html

.. _lts_02_0004:

Querying a Log Group
====================

Function
--------

This function describes how to query a log group you have created to obtain its name, ID, expiration time, and creation time.

URI
---

-  URI format

   GET /v2.0/{project_id}/log-groups/{group_id}

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= ====== ============
      Parameter  Mandatory Type   Description
      ========== ========= ====== ============
      project_id Yes       String Project ID
      group_id   Yes       String Log group ID
      ========== ========= ====== ============

Request
-------

-  Request parameters

   None

-  Example request

   .. code-block:: text

      GET /v2.0/{project_id}/log-groups/{group_id}

Response
--------

-  Response parameters

   .. table:: **Table 2** Parameter description

      ============== ============= ====== ====================================
      Parameter      Sub-Parameter Type   Description
      ============== ============= ====== ====================================
      log_group_id   ``-``         String Log group ID
      log_group_name ``-``         String Log group name
      creation_time  ``-``         Int64  Log group creation time
      ttl_in_days    ``-``         Int    Log expiration time
      stream_size    ``-``         Int    Number of log streams in a log group
      ============== ============= ====== ====================================

-  Example response

   .. code-block::

      {
                  "log_group_id": "8ac95c07-357b-11e9-bc2a-286ed488ce71",
                  "log_group_name": "lts-group-3h0y",
                  "creation_time": 1550714033721,
                  "stream_size ": 0,
                  "ttl_in_days": 7
      }

Returned Value
--------------

-  Normal

   200

-  Abnormal

   For details, see :ref:`Status Codes <lts_api_0020>`.
