.. _get-list-domain-trusts:

List domain trusts
~~~~~~~~~~~~~~~~~~

.. code::

    GET /v2.0/RAX-AUTH/trusts

Retrieves a list of domain trusts.

..  note::

    - Users with the role ``identity:domain-trust-admin`` can list all domain
      trust. The result is limited to the first 1000 domain trusts.
    - If the caller listing the domain trusts is a user-admin or sub-user, the
      list filters to domain trust where the caller's domain is either the
      principal or delegate domain ID on the trust.
    - This API operation is implemented through the RAX-AUTH extension to the
      core Identity API.

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

The following table shows the query parameters for the request:

.. csv-table::
  :header: Name, Description
  :widths: auto

    delegateDomain, "The delegate domain for the domain trusts."
    principalDomain, "The principal domain for the domain trusts."

**Example: List domain trusts: JSON request**

.. code::

    GET /v2.0/RAX-AUTH/trusts
    Host: identity.api.rackspacecloud.com
    Accept: application/json
    Content-type: application/json
    X-Auth-Token: c6f56a1d89274da4b14c1de36c412345

This operation does not accept a request body.

--------
Response
--------

**Example: List a domain trusts JSON response**

.. code::

    HTTP/1.1 200 OK
    Content-Type: application/json

    {
        "domainTrusts": [
            {
                "delegateDomain": "07f25c743f204778977804618e39f817",
                "id": "f97e9b424a154f38a4989732c69a9a10",
                "name": "DomainTrust123",
                "principalDomain": "5aada1b7838c4366898d64654313ac81",
                "description": "Domain trust to give users observer and ticketing permissions",
            },
            {
                "delegateDomain": "bb20e710e60a4b0f9c02fe681b2b17cc",
                "id": "c7508b68e8264d078409823865d532ff",
                "name": "DomainTrust456",
                "principalDomain": "8896222c5a644a3f85a228bd90382d24",
                "description": "Another domain trust.",
            }
        ]
    }
