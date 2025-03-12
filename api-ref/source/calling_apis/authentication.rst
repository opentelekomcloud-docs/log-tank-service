:original_name: lts_api_0005.html

.. _lts_api_0005:

Authentication
==============

You can use either of the following authentication methods when calling APIs:

-  Token-based authentication: Requests are authenticated using a token.
-  AK/SK-based authentication: Requests are authenticated by encrypting the request body using an AK/SK pair. AK/SK-based authentication is recommended because it is more secure than token-based authentication.

Token-based Authentication
--------------------------

.. note::

   The validity period of a token is 24 hours. When using a token for authentication, cache it to prevent frequently calling the IAM API used to obtain a user token.

A token is used to acquire temporary permissions. During API authentication using a token, the token is added to requests to get permissions for calling the API.

You can obtain a token by calling the `Obtaining User Token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__ API. When you call the API, set **auth.scope** in the request body to **project**.

.. code-block::

   {
       "auth": {
           "identity": {
               "methods": [
                   "password"
               ],
               "password": {
                   "user": {
                       "name": "username",
                       "password": "********",
                       "domain": {
                           "name": "domainname"
                       }
                   }
               }
           },
           "scope": {
               "project": {
                   "name": "xxxxxxxx"
               }
           }
       }
   }

After a token is obtained, the **X-Auth-Token** header field must be added to requests to specify the token when calling other APIs. For example, if the token is **ABCDEFJ....**, **X-Auth-Token: ABCDEFJ....** can be added to a request as follows:

.. code-block::

   Content-Type: application/json
   X-Auth-Token: ABCDEFJ....

AK/SK-based Authentication
--------------------------

.. note::

   AK/SK-based authentication supports API requests with a body no larger than 12 MB. For API requests with a larger body, you should use token-based authentication.

In AK/SK-based authentication, AK/SK is used to sign requests and the signature is then added to the requests for authentication.

-  AK: access key ID, which is a unique identifier used in conjunction with a secret access key to sign requests cryptographically.
-  SK: secret access key used in conjunction with an AK to sign requests cryptographically. It identifies a request sender and prevents the request from being modified.

In AK/SK-based authentication, you can use an AK/SK to sign requests based on the signature algorithm or use the signing SDK to sign requests.

.. important::

   The signing SDK is only used for signing requests and is different from the SDKs provided by services.
