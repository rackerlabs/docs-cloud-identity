.. _get-identity-provider-mapping-policy-v2.0:

Get IDP mapping policy
~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

   GET /v2.0/RAX-AUTH/federation/identity-providers/{identityProviderId}/mapping

Get mapping policy for identity provider.

.. note::

   - Only JSON and YAML formats are allowed for IDP mapping policy. Accept
     type must be either `application/json` or `text/yaml`.

This table shows the possible response codes for this operation:

.. csv-table::
   :header: Response code, Name, Description
   :widths: auto

   200, OK, The request has been fulfilled.
   400, Bad Request, "The request is missing one or more elements, or
   the values of some elements are invalid."
   401, Unauthorized, "You are not authorized to complete this operation.
   This error can occur if the request is submitted with an invalid
   authentication token."
   403, Forbidden, "The request was valid, but the server is refusing to
   respond because you do not have permission to access the requested
   resource. Submit a request to your account administrator to
   determine how to gain access."
   404, Not Found, The requested resource was not found.
   405, Invalid Method, "The method specified in the request is not valid for
   the resource identified in the request URI."
   406, Not Acceptable, The server cannot send data in a format requested.
   413, Over Limit, The number of items returned is above the allowed limit.
   503, Service Fault, Service is not available.

Request
-------

This table shows the header parameters for the request:

.. csv-table::
   :header: Name, Type, Description
   :widths: auto

   X-Auth-Token, String *(Required)*, A valid authentication token.

This table shows the URI parameters for the request:

.. csv-table::
   :header: Name, Type, Description
   :widths: auto

   {identityProviderId}, String *(Required)*, The Identity Provider's ID.

Response
--------

**Example: Get IDP mapping policy response: JSON**

.. code::

   {
       "property":{
           "value":"default policy"
       }
   }

**Example: Get IDP mapping policy response: YAML**

.. code::

   ---
   property:
      value: default policy
