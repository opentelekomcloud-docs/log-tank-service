:original_name: lts_02_0005.html

.. _lts_02_0005:

Deleting a Log Group
====================

Function
--------

This function describes how to delete a log group that will not be used.

.. note::

   Before deleting a log group, ensure that the log group has no log transfer tasks. Deleted log groups cannot be recovered. Therefore, exercise caution when performing this deletion operation.

URI
---

-  URI format

   DELETE /v2.0/{project_id}/log-groups/{group_id}

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

   None

-  Example request

   .. code-block:: text

      DELETE /v2.0/{project_id}/log-groups/{group_id}

Response
--------

-  Response parameters

   None

-  Example response

   None

Returned Value
--------------

-  Normal

   204

-  Abnormal

   For details, see :ref:`Status Codes <lts_api_0020>`.
