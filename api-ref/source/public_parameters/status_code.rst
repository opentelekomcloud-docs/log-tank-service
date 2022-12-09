:original_name: lts_02_0020.html

.. _lts_02_0020:

Status Code
===========

:ref:`Table 1 <lts_02_0020__ref520876711>` lists the status code.

.. _lts_02_0020__ref520876711:

.. table:: **Table 1** Status code description

   +-------------+-----------------------+-------------------------------------------------------------------+
   | Status Code | Returned Value        | Description                                                       |
   +=============+=======================+===================================================================+
   | 200         | OK                    | The results of GET and PUT operations are returned normally.      |
   +-------------+-----------------------+-------------------------------------------------------------------+
   | 201         | OK                    | The POST request is successful and the query result is returned.  |
   +-------------+-----------------------+-------------------------------------------------------------------+
   | 204         | No Content            | The result of the DELETE operation is returned normally.          |
   +-------------+-----------------------+-------------------------------------------------------------------+
   | 400         | Bad Request           | Request error.                                                    |
   +-------------+-----------------------+-------------------------------------------------------------------+
   | 401         | Unauthorized          | The authentication information is not provided or is incorrect.   |
   +-------------+-----------------------+-------------------------------------------------------------------+
   | 403         | Forbidden             | You are forbidden to access the requested page.                   |
   +-------------+-----------------------+-------------------------------------------------------------------+
   | 404         | Not Found             | The server failed to find the requested resource.                 |
   +-------------+-----------------------+-------------------------------------------------------------------+
   | 408         | Request Timeout       | The request timed out.                                            |
   +-------------+-----------------------+-------------------------------------------------------------------+
   | 429         | Too Many Requests     | The number of requests exceeds the upper limit.                   |
   +-------------+-----------------------+-------------------------------------------------------------------+
   | 500         | Internal Server Error | Failed to complete the request because of a service error.        |
   +-------------+-----------------------+-------------------------------------------------------------------+
   | 503         | Service Unavailable   | Failed to complete the request because the system is unavailable. |
   +-------------+-----------------------+-------------------------------------------------------------------+
