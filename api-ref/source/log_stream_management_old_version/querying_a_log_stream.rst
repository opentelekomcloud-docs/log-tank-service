:original_name: lts_02_0008.html

.. _lts_02_0008:

Querying a Log Stream
=====================

Function
--------

This function describes how to query a log stream you have created to obtain its name, ID, expiration time, and creation time.

URI
---

-  URI format

   GET /v2.0/{project_id}/log-groups/{group_id}/log-topics/{topic_id}

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= ====== ==================
      Parameter  Mandatory Type   Description
      ========== ========= ====== ==================
      project_id Yes       String Project ID
      group_id   Yes       String Log group ID
      topic_id   Yes       String ID of a log stream
      ========== ========= ====== ==================

Request
-------

-  Request parameters

   None

-  Example request

   .. code-block:: text

      GET /v2.0/{project_id}/log-groups/{group_id}/log-topics/{topic_id}

Response
--------

-  Response parameters

   .. table:: **Table 2** Parameter description

      ============== ============= ====== =======================
      Parameter      Sub-Parameter Type   Description
      ============== ============= ====== =======================
      log_topic_name ``-``         String Log stream name
      creation_time  ``-``         Int64  Log group creation time
      index_enabled  ``-``         Bool   Search switch
      ============== ============= ====== =======================

-  Example response

   .. code-block::

      {
             "log_topic_name": "lts-topic-jgpv",
             "creation_time": 1550803822973,
             "index_enabled": true
      }

Returned Value
--------------

-  Normal

   200

-  Abnormal

   For details, see :ref:`Status Code <lts_02_0020>`.
