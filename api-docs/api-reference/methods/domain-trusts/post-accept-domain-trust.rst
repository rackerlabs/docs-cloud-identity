.. _post-accept-domain-trust:

Accept domain trust
~~~~~~~~~~~~~~~~~~~

.. code::

    POST /v2.0/RAX-AUTH/trusts/{domainTrustId}/accept

Accept a domain trust.

.. note::

    - A user-admin and user-manager can accept a trust if their domain matches
      the delegate domain on the trust.
    - Users with the role ``identity:domain-trust-admin`` can accept domain
      trusts for any principal and delegate domain.
    - Use the RAX-AUTH API extension to the Core Identity API to implement this
      API operation.

The following table shows the possible response codes for this operation:

.. csv-table::
  :header: Response Code, Name, Description
  :widths: 2, 2, 2

  204, OK, The request succeeded.
  400, Bad Request, The request was invalid.
  401, Unauthorized, You are not authorized to complete this operation. This error can occur if the request is submitted with an invalid authentication token.
  403, Forbidden, Caller does not have an appropriate role.
  404, Not Found, The requested resource was not found.
  405, Invalid Method, The method specified in the request is not valid for the resource identified in the request URI.
  503, Service Fault, Service is not available.

-------
Request
-------

The following table shows the header parameters for the request:

.. csv-table::
  :header: Name, Type, Description
  :widths: 2, 2, 2

  X-Auth-Token, String *(Required)*, A valid authentication token for a user.

The following table shows the URI path parameters for the request:

.. csv-table::
  :header: Name, Description
  :widths: auto

  domainTrustId, The ID of the domain trust you want to get.

The following table shows the body parameters for the request:

.. csv-table::
  :header: Name, Type, Description
  :widths: 2, 2, 2

  **acceptCode**, Object *(Required)*, An object containing the domain trust accept code.
  acceptCode.\ **code**, String *(Required)*, The code to accept a domain trust.

**Example: Accept domain trust JSON Request**

.. code::

    {
        "acceptCode": {
            "code": "LYB7GJNC85"
        }
    }

--------
Response
--------
This operation doesn't return a response body.
