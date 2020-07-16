.. _get-a-domain-trust:

Retrieve a domain trust
~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /v2.0/RAX-AUTH/trusts/{domainTrustId}

Retrieves the specified domain trust by ID.

..  note::

    - Users with the ``identity:user-admin`` and ``identity:user-manage`` role
      can get a domain trust where their domain ID is either the principal or
      delegate domain on the domain trust.
    - Users with the role ``identity:domain-trust-admin`` can get any domain
      trust.
    - Use the RAX-AUTH API extension to the Core Identity API to implement this
      API operation.

The following table shows the possible response codes for this operation:

.. csv-table::
   :header: Response code, Name, Description
   :widths: auto

    200, OK, The request succeeded.
    400, Bad Request, The request was invalid.
    401, Unauthorized, "You are not authorized to complete this, operation. This error can occur if the, request is submitted with an invalid, authentication token."
    403, Forbidden, Caller does not have an appropriate role.
    404, Not Found, The requested resource was not found.
    405, Invalid Method, The method specified in the request is not valid for the resource identified in the request URI.
    503, Service Fault, Service is not available.

-------
Request
-------

The following table shows the header parameters for the get a domain trust
request:

.. csv-table::
   :header: Name, Type, Description
   :widths: auto

    X-Auth-Token, String *(Required)*, A valid authentication token.

The following table shows the URI parameters for the get a domain trust
request:

.. csv-table::
   :header: Name, Type, Description
   :widths: auto

    {domainTrustId}, String, A domain trust ID.

**Example: Get a domain trust: JSON request**

.. code::

    GET /v2.0/RAX-AUTH/trusts/123456
    Host: identity.api.rackspacecloud.com
    Accept: application/json
    Content-type: application/json
    X-Auth-Token: c6f56a1d89274da4b14c1de36c412345

This operation does not accept a request body.

--------
Response
--------

**Example: Get a domain trust JSON response**

.. code::

    HTTP/1.1 200 OK
    Content-Type: application/json

    {
        "domainTrust": {
            "id": "123456",
            "delegateDomain": "200",
            "name": "domainTrust26905",
            "principalDomain": "100",
            "description": "Domain trust to give users observer permissions",
        }
    }
