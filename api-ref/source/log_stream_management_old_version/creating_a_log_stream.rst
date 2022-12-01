:original_name: lts_02_0007.html

.. _lts_02_0007:

Creating a Log Stream
=====================

Function
--------

This function describes how to create a log stream under a created log group. You can view and query raw logs under a log stream.

URI
---

-  URI format

   POST /v2.0/{project_id}/log-groups/{group_id}/log-topics

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= ====== =========================
      Parameter  Mandatory Type   Description
      ========== ========= ====== =========================
      project_id Yes       String Project ID
      group_id   Yes       String ID of a created log group
      ========== ========= ====== =========================

Request
-------

-  Request parameters

   .. table:: **Table 2** Parameter description

      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                     |
      +=================+=================+=================+=================================================================================================================================+
      | log_topic_name  | Yes             | String          | Log stream name.                                                                                                                |
      |                 |                 |                 |                                                                                                                                 |
      |                 |                 |                 | The configuration rules are as follows:                                                                                         |
      |                 |                 |                 |                                                                                                                                 |
      |                 |                 |                 | -  Must be a string of 1 to 64 characters.                                                                                      |
      |                 |                 |                 | -  Only letters, digits, underscores (_), hyphens (-), and periods (.) are allowed. The name cannot start or end with a period. |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block:: text

      POST
      /v2.0/{project_id}/log-groups/{group_id}/log-topics
      {
      "log_topic_name":"testTopic01"
      }

Response
--------

-  Response parameters

   .. table:: **Table 3** Parameter description

      ============ ====== ==================
      Parameter    Type   Description
      ============ ====== ==================
      log_topic_id String ID of a log stream
      ============ ====== ==================

-  Example response

   .. code-block::

      {
         "log_topic_id":"a25d64c8-3028-11e9-9660-286ed488ce71"
      }

Returned Value
--------------

-  Normal

   201

-  Abnormal

   For details about status code, see :ref:`Status Code <lts_02_0020>`.
