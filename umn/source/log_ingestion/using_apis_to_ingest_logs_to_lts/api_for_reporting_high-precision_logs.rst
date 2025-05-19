:original_name: lts_04_0217.html

.. _lts_04_0217:

API for Reporting High-Precision Logs
=====================================

Function
--------

This API is used to report tenant logs from a host to LTS.

The access IP address is contained in the ICAgent installation command displayed on the LTS console. The port number is 8102. You can check the :ref:`Example Request <lts_04_0217__en-us_topic_0000001098327000_en-us_topic_0000001133002307_section1475015224126>` to see how to add the access IP address and port number in a request.

Each log event will carry a nanosecond-level timestamp when it is reported. When you view logs on the LTS console, the log events are sorted by timestamp.

URI
---

POST /v2/{project_id}/lts/groups/{log_group_id}/streams/{log_stream_id}/tenant/contents/high-accuracy

.. table:: **Table 1** URI parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                               |
   +=================+=================+=================+===========================================================================================================================================================================================================================================================================================+
   | project_id      | Yes             | String          | Project ID. For details about how to obtain it, see `Obtaining the Account ID, Project ID, Log Group ID, and Log Stream ID <https://docs.otc.t-systems.com/log-tank-service/api-ref/appendix/obtaining_the_account_id_project_id_log_group_id_and_log_stream_id.html#lts-api-0006>`__.    |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                           |
   |                 |                 |                 | Value length: 32 characters                                                                                                                                                                                                                                                               |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_group_id    | Yes             | String          | Log group ID. For details about how to obtain it, see `Obtaining the Account ID, Project ID, Log Group ID, and Log Stream ID <https://docs.otc.t-systems.com/log-tank-service/api-ref/appendix/obtaining_the_account_id_project_id_log_group_id_and_log_stream_id.html#lts-api-0006>`__.  |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                           |
   |                 |                 |                 | Value length: 36 characters                                                                                                                                                                                                                                                               |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_stream_id   | Yes             | String          | Log stream ID. For details about how to obtain it, see `Obtaining the Account ID, Project ID, Log Group ID, and Log Stream ID <https://docs.otc.t-systems.com/log-tank-service/api-ref/appendix/obtaining_the_account_id_project_id_log_group_id_and_log_stream_id.html#lts-api-0006>`__. |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                           |
   |                 |                 |                 | Value length: 36 characters                                                                                                                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                           |
   |                 |                 |                 | A write rate exceeding 100 MB/s per log stream may cause log losses.                                                                                                                                                                                                                      |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +------------------+-----------------+-----------------+-----------------------------------------------------------+
   | Parameter        | Mandatory       | Type            | Description                                               |
   +==================+=================+=================+===========================================================+
   | X-Auth-Token     | Yes             | String          | Indicates the user token obtained from IAM.               |
   |                  |                 |                 |                                                           |
   |                  |                 |                 | Minimum length: 1,000 characters                          |
   |                  |                 |                 |                                                           |
   |                  |                 |                 | Maximum length: 2,000 characters                          |
   +------------------+-----------------+-----------------+-----------------------------------------------------------+
   | Content-Type     | Yes             | String          | Set this parameter to **application/json;charset=UTF-8**. |
   |                  |                 |                 |                                                           |
   |                  |                 |                 | Minimum length: 30 characters                             |
   |                  |                 |                 |                                                           |
   |                  |                 |                 | Maximum length: 30 characters                             |
   +------------------+-----------------+-----------------+-----------------------------------------------------------+
   | Content-Encoding | No              | String          | Log compression format.                                   |
   |                  |                 |                 |                                                           |
   |                  |                 |                 | Example value:                                            |
   |                  |                 |                 |                                                           |
   |                  |                 |                 | -  **GZIP**                                               |
   |                  |                 |                 | -  **SNAPPY**                                             |
   |                  |                 |                 | -  **gzip**                                               |
   |                  |                 |                 | -  **snappy**                                             |
   +------------------+-----------------+-----------------+-----------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-------------------+-----------+---------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory | Type                                                                                                                      | Description                                                                                                                                                                                                                                                                                   |
   +===================+===========+===========================================================================================================================+===============================================================================================================================================================================================================================================================================================+
   | contents          | Yes       | Array of :ref:`LogContents <lts_04_0217__en-us_topic_0000001098327000_en-us_topic_0000001133002307_response_logcontents>` | Indicates a list of log events that carry reporting timestamps.                                                                                                                                                                                                                               |
   +-------------------+-----------+---------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | labels            | Yes       | Object                                                                                                                    | Custom labels.                                                                                                                                                                                                                                                                                |
   +-------------------+-----------+---------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tenant_project_id | No        | String                                                                                                                    | Tenant project ID. For details about how to obtain it, see `Obtaining the Account ID, Project ID, Log Group ID, and Log Stream ID <https://docs.otc.t-systems.com/log-tank-service/api-ref/appendix/obtaining_the_account_id_project_id_log_group_id_and_log_stream_id.html#lts-api-0006>`__. |
   +-------------------+-----------+---------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _lts_04_0217__en-us_topic_0000001098327000_en-us_topic_0000001133002307_response_logcontents:

.. table:: **Table 4** LogContents

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                            |
   +=================+=================+=================+========================================================================================================================================================================================================+
   | log_time_ns     | Yes             | Long            | Time when log data is reported (UTC time in nanoseconds).                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                        |
   |                 |                 |                 | When logs are reported to LTS via APIs, the time difference between the log reporting time you set and the current time must not exceed two days. Otherwise, the reported logs will be deleted by LTS. |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log             | Yes             | String          | Log content.                                                                                                                                                                                           |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

When the status code is **200**, the response parameters are as follows:

.. table:: **Table 5** Response body parameters

   ========= ====== ================
   Parameter Type   Description
   ========= ====== ================
   errorCode String Error code.
   error_msg String Error message.
   result    String Response result.
   ========= ====== ================

When the status code is **400**, the response parameters are as follows:

.. table:: **Table 6** Response body parameters

   ========= ====== ================
   Parameter Type   Description
   ========= ====== ================
   errorCode String Error code.
   error_msg String Error message.
   result    String Response result.
   ========= ====== ================

When the status code is **401**, the response parameters are as follows:

.. table:: **Table 7** Response body parameters

   ========= ====== ================
   Parameter Type   Description
   ========= ====== ================
   errorCode String Error code.
   error_msg String Error message.
   result    String Response result.
   ========= ====== ================

When the status code is **500**, the response parameters are as follows:

.. table:: **Table 8** Response body parameters

   ========= ====== ================
   Parameter Type   Description
   ========= ====== ================
   errorCode String Error code.
   error_msg String Error message.
   result    String Response result.
   ========= ====== ================

When the status code is **503**, the response parameter is as follows:

.. table:: **Table 9** Response body parameter

   ========= ====== =====================================
   Parameter Type   Description
   ========= ====== =====================================
   result    String The requested service is unavailable.
   ========= ====== =====================================

.. _lts_04_0217__en-us_topic_0000001098327000_en-us_topic_0000001133002307_section1475015224126:

Example Request
---------------

.. code-block:: text

   POST https://{access_IP_address:8102}/v2/{project_id}/lts/groups/{log_group_id}/streams/{log_stream_id}/tenant/contents/high-accuracy

   {
       "contents": [
           {
               "log_time_ns": 1586850540000000000,
               "log": "Fri Feb  15 15:48:04 UTC 2019"
           },
           {
               "log_time_ns": 1586850540000000001,
               "log": "Sat April 18 16:04:04 UTC 2019"
           }
       ],
       "labels": {
           "user_tag": "string"
       }
   }

Example Response
----------------

Example response with status code **200**:

Logs are reported.

.. code-block::

   {
     "errorCode": "SVCSTG.ALS.200.200",
     "error_msg": "Report success.",
     "result": null
   }

Example response with status code **401**:

The authentication information is incorrect or invalid.

.. code-block::

   {
     "errorCode" : "SVCSTG.ALS.403.105",
     "error_msg" : "Project id is invalid.",
     "result": null
   }

Status Code
-----------

+-------------+------------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                          |
+=============+======================================================================================================+
| 200         | The request has succeeded.                                                                           |
+-------------+------------------------------------------------------------------------------------------------------+
| 400         | The request is invalid. Modify the request based on the description in **error_msg** before a retry. |
+-------------+------------------------------------------------------------------------------------------------------+
| 401         | The authentication information is incorrect or invalid.                                              |
+-------------+------------------------------------------------------------------------------------------------------+
| 500         | An internal error occurred.                                                                          |
+-------------+------------------------------------------------------------------------------------------------------+
| 503         | The requested service is unavailable.                                                                |
+-------------+------------------------------------------------------------------------------------------------------+
