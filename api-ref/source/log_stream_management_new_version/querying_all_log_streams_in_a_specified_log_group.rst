:original_name: lts_api_0017.html

.. _lts_api_0017:

Querying All Log Streams in a Specified Log Group
=================================================

Function
--------

This API is used to query information about all log streams in a specified log group.

URI
---

GET /v2/{project_id}/groups/{log_group_id}/streams

.. table:: **Table 1** URI parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                             |
   +=================+=================+=================+=========================================================================================================================================================================+
   | project_id      | Yes             | String          | Project ID. For details about how to obtain the ID, see :ref:`Obtaining the AccountID, Project ID, Log Group ID, and Log Stream ID <lts_api_0006>`. Default value: None |
   |                 |                 |                 |                                                                                                                                                                         |
   |                 |                 |                 | Value length: 32 characters                                                                                                                                             |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_group_id    | Yes             | String          | ID of the log group whose log streams will be queried.                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                         |
   |                 |                 |                 | Default value: None                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                         |
   |                 |                 |                 | Value length: 36 characters                                                                                                                                             |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                               |
   +=================+=================+=================+===========================================================+
   | X-Auth-Token    | Yes             | String          | User token obtained from IAM.                             |
   |                 |                 |                 |                                                           |
   |                 |                 |                 | Default value: None                                       |
   |                 |                 |                 |                                                           |
   |                 |                 |                 | Minimum length: 1000 characters                           |
   |                 |                 |                 |                                                           |
   |                 |                 |                 | Maximum length: 2000 characters                           |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------+
   | Content-Type    | Yes             | String          | Set this parameter to **application/json;charset=UTF-8**. |
   |                 |                 |                 |                                                           |
   |                 |                 |                 | Default value: None                                       |
   |                 |                 |                 |                                                           |
   |                 |                 |                 | Minimum length: 30 characters                             |
   |                 |                 |                 |                                                           |
   |                 |                 |                 | Maximum length: 30 characters                             |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameter

   +-------------+---------------------------------------------------------------------------------------------+----------------------+
   | Parameter   | Type                                                                                        | Description          |
   +=============+=============================================================================================+======================+
   | log_streams | Array of :ref:`LogStream <lts_api_0017__en-us_topic_0162710089_response_logstream>` objects | List of log streams. |
   +-------------+---------------------------------------------------------------------------------------------+----------------------+

.. _lts_api_0017__en-us_topic_0162710089_response_logstream:

.. table:: **Table 4** LogStream

   +-----------------------+-----------------------+----------------------------------+
   | Parameter             | Type                  | Description                      |
   +=======================+=======================+==================================+
   | creation_time         | long                  | Creation time.                   |
   |                       |                       |                                  |
   |                       |                       | Minimum value: **1577808000000** |
   |                       |                       |                                  |
   |                       |                       | Maximum value: **4102416000000** |
   +-----------------------+-----------------------+----------------------------------+
   | log_stream_name       | String                | Log stream name.                 |
   |                       |                       |                                  |
   |                       |                       | Value length: 36 characters      |
   +-----------------------+-----------------------+----------------------------------+
   | log_stream_id         | String                | Log stream ID.                   |
   |                       |                       |                                  |
   |                       |                       | Value length: 36 characters      |
   +-----------------------+-----------------------+----------------------------------+
   | filter_count          | Integer               | Number of filters.               |
   |                       |                       |                                  |
   |                       |                       | Minimum value: **0**             |
   |                       |                       |                                  |
   |                       |                       | Maximum value: **5**             |
   +-----------------------+-----------------------+----------------------------------+
   | tag                   | Map<String,String>    | Log stream tag.                  |
   +-----------------------+-----------------------+----------------------------------+

**Status code: 401**

.. table:: **Table 5** Response body parameters

   +-----------------------+-----------------------+--------------------------+
   | Parameter             | Type                  | Description              |
   +=======================+=======================+==========================+
   | error_code            | String                | Error code.              |
   |                       |                       |                          |
   |                       |                       | Enumerated value:        |
   |                       |                       |                          |
   |                       |                       | -  **LTS.0403**          |
   +-----------------------+-----------------------+--------------------------+
   | error_msg             | String                | Error message.           |
   |                       |                       |                          |
   |                       |                       | Enumerated value:        |
   |                       |                       |                          |
   |                       |                       | -  **Invalid projectId** |
   +-----------------------+-----------------------+--------------------------+

**Status code: 403**

.. table:: **Table 6** Response body parameters

   +-----------------------+-----------------------+--------------------------+
   | Parameter             | Type                  | Description              |
   +=======================+=======================+==========================+
   | error_code            | String                | Error code.              |
   |                       |                       |                          |
   |                       |                       | Enumerated value:        |
   |                       |                       |                          |
   |                       |                       | -  **LTS.0403**          |
   +-----------------------+-----------------------+--------------------------+
   | error_msg             | String                | Error message.           |
   |                       |                       |                          |
   |                       |                       | Enumerated value:        |
   |                       |                       |                          |
   |                       |                       | -  **Invalid projectId** |
   +-----------------------+-----------------------+--------------------------+

**Status code: 500**

.. table:: **Table 7** Response body parameters

   +-----------------------+-----------------------+--------------------------+
   | Parameter             | Type                  | Description              |
   +=======================+=======================+==========================+
   | error_code            | String                | Error code.              |
   |                       |                       |                          |
   |                       |                       | Enumerated value:        |
   |                       |                       |                          |
   |                       |                       | -  **LTS.0403**          |
   +-----------------------+-----------------------+--------------------------+
   | error_msg             | String                | Error message.           |
   |                       |                       |                          |
   |                       |                       | Enumerated value:        |
   |                       |                       |                          |
   |                       |                       | -  **Invalid projectId** |
   +-----------------------+-----------------------+--------------------------+

**Status code: 503**

.. table:: **Table 8** Response body parameter

   ========= ====== =====================================
   Parameter Type   Description
   ========= ====== =====================================
   ``-``     String The requested service is unavailable.
   ========= ====== =====================================

Example Request
---------------

.. code-block:: text

   GET https://{endpoint}/v2/{project_id}/groups/{log_group_id}/streams

   /v2/{project_id}/groups/{log_group_id}/streams

Example Response
----------------

**Status code: 200**

.. code-block::

   {
     "log_streams" : [ {
       "creation_time":1630549842955,
       "log_stream_name":"lts-stream-02kh",
       "log_stream_id":"c54dbc58-0fd8-48ed-b007-6d54981427a7",
       "filter_count":0
        } ]
   }

**Status code: 401**

Authentication failed. Check the token and try again.

.. code-block::

   {
     "error_code" : "LTS.0003",
     "error_msg" : "Invalid token"
   }

**Status code: 403**

The server understood the request but refused to authorize it. The client should not repeat the request without modifications.

.. code-block::

   {
     "error_code" : "LTS.0001",
     "error_msg" : "Invalid projectId"
   }

**Status code: 500**

The server has received the request but encountered an internal error.

.. code-block::

   {
     "error_code" : "LTS.0010",
     "error_msg" : "The system encountered an internal error"
   }

Status Codes
------------

+-------------+--------------------------------------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                                                    |
+=============+================================================================================================================================+
| 200         | The request is successful.                                                                                                     |
+-------------+--------------------------------------------------------------------------------------------------------------------------------+
| 401         | Authentication failed. Check the token and try again.                                                                          |
+-------------+--------------------------------------------------------------------------------------------------------------------------------+
| 403         | The server understood the request but refused to authorize it. The client should not repeat the request without modifications. |
+-------------+--------------------------------------------------------------------------------------------------------------------------------+
| 500         | The server has received the request but encountered an internal error.                                                         |
+-------------+--------------------------------------------------------------------------------------------------------------------------------+
| 503         | The requested service is unavailable.                                                                                          |
+-------------+--------------------------------------------------------------------------------------------------------------------------------+

Error Codes
-----------

For details, see :ref:`Error Codes <lts_02_0021>`.
