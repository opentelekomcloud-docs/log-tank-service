:original_name: Deletefavorite.html

.. _Deletefavorite:

Removing a Resource from Favorites
==================================

Function
--------

This API is used to remove a specified resource from favorites.

URI
---

DELETE /v1.0/{project_id}/lts/favorite/{fav_res_id}

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
   | fav_res_id      | Yes             | String          | ID of a favorite resource, including its log group or stream.                                                                                              |
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

   +-----------+----------------------------------------------------------------------------+---------------------+
   | Parameter | Type                                                                       | Description         |
   +===========+============================================================================+=====================+
   | message   | :ref:`ErrorMessagebody <deletefavorite__response_errormessagebody>` object | Error message body. |
   +-----------+----------------------------------------------------------------------------+---------------------+

.. _deletefavorite__response_errormessagebody:

.. table:: **Table 4** ErrorMessagebody

   ========= ====== ==============
   Parameter Type   Description
   ========= ====== ==============
   code      String Error code.
   details   String Error message.
   ========= ====== ==============

**Status code: 400**

.. table:: **Table 5** Response body parameters

   +-----------+------------------------------------------------------------------------------+---------------------+
   | Parameter | Type                                                                         | Description         |
   +===========+==============================================================================+=====================+
   | message   | :ref:`ErrorMessagebody <deletefavorite__response_errormessagebody_1>` object | Error message body. |
   +-----------+------------------------------------------------------------------------------+---------------------+

.. _deletefavorite__response_errormessagebody_1:

.. table:: **Table 6** ErrorMessagebody

   ========= ====== ==============
   Parameter Type   Description
   ========= ====== ==============
   code      String Error code.
   details   String Error message.
   ========= ====== ==============

**Status code: 500**

.. table:: **Table 7** Response body parameters

   +-----------+------------------------------------------------------------------------------+---------------------+
   | Parameter | Type                                                                         | Description         |
   +===========+==============================================================================+=====================+
   | message   | :ref:`ErrorMessagebody <deletefavorite__response_errormessagebody_2>` object | Error message body. |
   +-----------+------------------------------------------------------------------------------+---------------------+

.. _deletefavorite__response_errormessagebody_2:

.. table:: **Table 8** ErrorMessagebody

   ========= ====== ==============
   Parameter Type   Description
   ========= ====== ==============
   code      String Error code.
   details   String Error message.
   ========= ====== ==============

Example Requests
----------------

Removing from Favorites

.. code-block:: text

   DELETE /v1.0/{project_id}/lts/favorite/{fav_res_id}

Example Responses
-----------------

**Status code: 200**

Removed from favorites.

.. code-block::

   none

**Status code: 400**

Invalid request. Modify the request based on the description in **error_msg** before a retry.

.. code-block::

   {
     "message" : {
       "code" : "LTS.0009",
       "details" : "update favorite failed"
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
| 200         | Removed from favorites.                                                                       |
+-------------+-----------------------------------------------------------------------------------------------+
| 400         | Invalid request. Modify the request based on the description in **error_msg** before a retry. |
+-------------+-----------------------------------------------------------------------------------------------+
| 500         | The server has received the request but encountered an internal error.                        |
+-------------+-----------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
