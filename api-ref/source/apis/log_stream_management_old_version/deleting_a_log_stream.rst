:original_name: lts_02_0009.html

.. _lts_02_0009:

Deleting a log stream
=====================

Function
--------

This function describes how to delete a log stream that will not be used.

.. note::

   Before deleting a log stream, ensure that the log stream has no log transfer tasks. Deleted log streams cannot be recovered. Therefore, exercise caution when performing this deletion operation.

URI
---

-  URI format

   DELETE /v2.0/{project_id}/log-groups/{group_id}/log-topics/{topic_id}

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= ====== ==========================
      Parameter  Mandatory Type   Description
      ========== ========= ====== ==========================
      project_id Yes       String Project ID
      group_id   Yes       String ID of a created log group
      topic_id   Yes       String ID of a created log stream
      ========== ========= ====== ==========================

Request
-------

-  Request parameters

   None

-  Example request

   .. code-block:: text

      DELETE /v2.0/{project_id}/log-groups/{group_id}/log-topics/{topic_id}

Response
--------

-  Parameter description

   None

-  Example response

   None

Returned Value
--------------

-  Normal

   204

-  Abnormal

   For details, see :ref:`Status Codes <lts_api_0020>`.
