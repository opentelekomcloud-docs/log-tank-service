:original_name: ListTopnTrafficStatistics.html

.. _ListTopnTrafficStatistics:

Collecting Traffic Statistics on Top N Log Groups or Log Streams
================================================================

Function
--------

This API is used to collect traffic statistics on top n log groups or log streams.

URI
---

POST /v2/{project_id}/lts/topn-traffic-statistics

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

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                   |
   +=================+=================+=================+===============================================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token obtained from IAM. For details about how to obtain a user token, see :ref:`Obtaining a User Token <lts_api_0004>`. |
   |                 |                 |                 |                                                                                                                               |
   |                 |                 |                 | Minimum: **1000**                                                                                                             |
   |                 |                 |                 |                                                                                                                               |
   |                 |                 |                 | Maximum: **2000**                                                                                                             |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type    | Yes             | String          | Set this parameter to application/json;charset=UTF-8.                                                                         |
   |                 |                 |                 |                                                                                                                               |
   |                 |                 |                 | Minimum: **30**                                                                                                               |
   |                 |                 |                 |                                                                                                                               |
   |                 |                 |                 | Maximum: **30**                                                                                                               |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+--------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type               | Description                                                                                                                                                                                                                                             |
   +=================+=================+====================+=========================================================================================================================================================================================================================================================+
   | end_time        | Yes             | Long               | End timestamp, in milliseconds.                                                                                                                                                                                                                         |
   +-----------------+-----------------+--------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | is_desc         | Yes             | Boolean            | Whether to sort data in descending order (**true** or **false**).                                                                                                                                                                                       |
   +-----------------+-----------------+--------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | resource_type   | Yes             | String             | Resource type.                                                                                                                                                                                                                                          |
   |                 |                 |                    |                                                                                                                                                                                                                                                         |
   |                 |                 |                    | **log_group**: log group                                                                                                                                                                                                                                |
   |                 |                 |                    |                                                                                                                                                                                                                                                         |
   |                 |                 |                    | **log_stream**: log stream                                                                                                                                                                                                                              |
   |                 |                 |                    |                                                                                                                                                                                                                                                         |
   |                 |                 |                    | **tenant**: tenant                                                                                                                                                                                                                                      |
   +-----------------+-----------------+--------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sort_by         | Yes             | String             | Sorting. Data to be sorted must exist in **search_list**.                                                                                                                                                                                               |
   |                 |                 |                    |                                                                                                                                                                                                                                                         |
   |                 |                 |                    | **index**: index                                                                                                                                                                                                                                        |
   |                 |                 |                    |                                                                                                                                                                                                                                                         |
   |                 |                 |                    | **write**: read and write                                                                                                                                                                                                                               |
   |                 |                 |                    |                                                                                                                                                                                                                                                         |
   |                 |                 |                    | **storage**: storage                                                                                                                                                                                                                                    |
   +-----------------+-----------------+--------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | start_time      | Yes             | Long               | Start timestamp of the query, in milliseconds. A maximum of 30 days are supported.                                                                                                                                                                      |
   +-----------------+-----------------+--------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | topn            | Yes             | Integer            | Number of data records to be queried. The value ranges from 1 to 100.                                                                                                                                                                                   |
   +-----------------+-----------------+--------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | filter          | Yes             | Map<String,String> | Filter, which is in a map structure with keys as filtering attributes and values as attribute values. It does not support fuzzy match. The format for filter criteria is {"key": "xxxxxx"}, where **key** can be **log_group_id** or **log_stream_id**. |
   +-----------------+-----------------+--------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | search_list     | Yes             | Array of strings   | Query data type. Multiple string arrays can be used together.                                                                                                                                                                                           |
   |                 |                 |                    |                                                                                                                                                                                                                                                         |
   |                 |                 |                    | **index**: index                                                                                                                                                                                                                                        |
   |                 |                 |                    |                                                                                                                                                                                                                                                         |
   |                 |                 |                    | **write**: read and write                                                                                                                                                                                                                               |
   |                 |                 |                    |                                                                                                                                                                                                                                                         |
   |                 |                 |                    | **storage**: storage                                                                                                                                                                                                                                    |
   +-----------------+-----------------+--------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+-----------------------------------------------------------------------------------------------+------------------+
   | Parameter | Type                                                                                          | Description      |
   +===========+===============================================================================================+==================+
   | results   | Array of :ref:`ResultsTopnBody <listtopntrafficstatistics__response_resultstopnbody>` objects | Response result. |
   +-----------+-----------------------------------------------------------------------------------------------+------------------+

.. _listtopntrafficstatistics__response_resultstopnbody:

.. table:: **Table 5** ResultsTopnBody

   +-----------------------+--------+---------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type   | Description                                                                                                   |
   +=======================+========+===============================================================================================================+
   | index_traffic         | Double | Index traffic, in bytes. This parameter is returned when the queried data type contains **index**.            |
   +-----------------------+--------+---------------------------------------------------------------------------------------------------------------+
   | storage               | Double | Storage capacity, in bytes. This parameter is returned when the queried data type contains **storage**.       |
   +-----------------------+--------+---------------------------------------------------------------------------------------------------------------+
   | write_traffic         | Double | Write traffic, in bytes. This parameter is returned when the queried data type contains **write**.            |
   +-----------------------+--------+---------------------------------------------------------------------------------------------------------------+
   | log_group_id          | String | Log group ID. This parameter is returned when the resource type is log group.                                 |
   +-----------------------+--------+---------------------------------------------------------------------------------------------------------------+
   | log_group_name        | String | Log group name. This parameter is returned when the resource type is log group.                               |
   +-----------------------+--------+---------------------------------------------------------------------------------------------------------------+
   | log_stream_id         | String | Log stream ID. This parameter is returned when the resource type is log stream.                               |
   +-----------------------+--------+---------------------------------------------------------------------------------------------------------------+
   | log_stream_name       | String | Log stream name. This parameter is returned when the resource type is log stream.                             |
   +-----------------------+--------+---------------------------------------------------------------------------------------------------------------+
   | log_group_name_alias  | String | Log group alias, which is the same as the log group name by default. The alias is preferentially displayed.   |
   +-----------------------+--------+---------------------------------------------------------------------------------------------------------------+
   | log_stream_name_alias | String | Log stream alias, which is the same as the log stream name by default. The alias is preferentially displayed. |
   +-----------------------+--------+---------------------------------------------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 6** Response body parameters

   ============ ====== ==============
   Parameter    Type   Description
   ============ ====== ==============
   errorCode    String Error code.
   errorMessage String Error message.
   ============ ====== ==============

**Status code: 500**

.. table:: **Table 7** Response body parameters

   ============ ====== ==============
   Parameter    Type   Description
   ============ ====== ==============
   errorCode    String Error code.
   errorMessage String Error message.
   ============ ====== ==============

Example Requests
----------------

Collecting Traffic Statistics on Top N Log Groups or Log Streams

.. code-block:: text

   POST /v2/2a473356cca5487f8373be891bffc1cf/lts/topn-traffic-statistics

   {
     "sort_by" : "storage",
     "is_desc" : true,
     "resource_type" : "log_stream",
     "filter" : { },
     "start_time" : 1668668183969,
     "end_time" : 1669272983969,
     "search_list" : [ "index", "write", "storage" ],
     "topn" : 100
   }

Example Responses
-----------------

**Status code: 200**

Query succeeded.

.. code-block::

   {
     "results" : [ {
       "index_traffic" : 0,
       "log_stream_id" : "6fd93d47-7630-4284-a622-311d0082f6bb",
       "log_stream_name" : "cmdb-cce-cluster",
       "storage" : 59810657587,
       "write_traffic" : 0
     }, {
       "index_traffic" : 0,
       "log_stream_id" : "504ec3dd-ac28-4783-babb-22a49f36afe3",
       "log_stream_name" : "CMSkaifatest",
       "storage" : 20033606015,
       "write_traffic" : 0
     }, {
       "index_traffic" : 6825703991,
       "log_stream_id" : "a14dacb0-5a13-43a8-89a3-ea5424d95133",
       "log_stream_name" : "ELB",
       "storage" : 15659303771,
       "write_traffic" : 1.3651407982E9
     }, {
       "index_traffic" : 302172889,
       "log_stream_id" : "25fe7494-7395-438e-8340-647613673ffa",
       "log_stream_name" : "LTStest-916-statefulset",
       "storage" : 316552589,
       "write_traffic" : 6.04345778E7
     }, {
       "index_traffic" : 0,
       "log_stream_id" : "956586fc-b828-44be-8672-0a323962a8fa",
       "log_stream_name" : "mongodb_slow",
       "storage" : 0,
       "write_traffic" : 0
     } ]
   }

**Status code: 400**

Invalid request. Modify the request based on the description in **error_msg** before a retry.

.. code-block::

   {
     "errorCode" : "LTS.0208",
     "errorMessage" : "The log stream does not existed"
   }

**Status code: 500**

The server has received the request but encountered an internal error.

.. code-block::

   {
     "errorCode" : "LTS.0203",
     "errorMessage" : "Internal Server Error"
   }

Status Codes
------------

+-------------+-----------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                   |
+=============+===============================================================================================+
| 200         | Query succeeded.                                                                              |
+-------------+-----------------------------------------------------------------------------------------------+
| 400         | Invalid request. Modify the request based on the description in **error_msg** before a retry. |
+-------------+-----------------------------------------------------------------------------------------------+
| 500         | The server has received the request but encountered an internal error.                        |
+-------------+-----------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
