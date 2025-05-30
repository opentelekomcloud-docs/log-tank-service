:original_name: lts_api_0020.html

.. _lts_api_0020:

Status Codes
============

:ref:`Table 1 <lts_api_0020__ref520876711>` lists the status codes.

.. _lts_api_0020__ref520876711:

.. table:: **Table 1** Status codes

   +-------------+-----------------------+------------------------------------------------------------------------------------------------+
   | Status Code | Returned Value        | Description                                                                                    |
   +=============+=======================+================================================================================================+
   | 200         | OK                    | The normal response for the GET or PUT operation is returned.                                  |
   +-------------+-----------------------+------------------------------------------------------------------------------------------------+
   | 201         | OK                    | The POST request is successful and the query result is returned.                               |
   +-------------+-----------------------+------------------------------------------------------------------------------------------------+
   | 204         | No Content            | The normal response for the DELETE operation is returned.                                      |
   +-------------+-----------------------+------------------------------------------------------------------------------------------------+
   | 400         | Bad Request           | Request error.                                                                                 |
   +-------------+-----------------------+------------------------------------------------------------------------------------------------+
   | 401         | Unauthorized          | The authentication information is not provided or is incorrect.                                |
   +-------------+-----------------------+------------------------------------------------------------------------------------------------+
   | 403         | Forbidden             | You are forbidden to access the page requested.                                                |
   +-------------+-----------------------+------------------------------------------------------------------------------------------------+
   | 404         | Not Found             | The server failed to find the requested resource.                                              |
   +-------------+-----------------------+------------------------------------------------------------------------------------------------+
   | 408         | Request Timeout       | The request timed out.                                                                         |
   +-------------+-----------------------+------------------------------------------------------------------------------------------------+
   | 429         | Too Many Requests     | The number of requests exceeded the upper limit.                                               |
   +-------------+-----------------------+------------------------------------------------------------------------------------------------+
   | 500         | Internal Server Error | The server encountered an unexpected condition which prevented it from fulfilling the request. |
   +-------------+-----------------------+------------------------------------------------------------------------------------------------+
   | 503         | Service Unavailable   | The service is currently unavailable.                                                          |
   +-------------+-----------------------+------------------------------------------------------------------------------------------------+
