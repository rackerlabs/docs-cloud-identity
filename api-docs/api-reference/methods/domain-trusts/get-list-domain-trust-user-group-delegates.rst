.. _get-list-domain-trust-user-group-delegates:

List domain trust user group delegates
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /v2.0/RAX-AUTH/trusts/{domainTrustId}/delegates/user-groups

Retrieves a list of domain trust user group delegates.

..  note::

    - A user-admin and user-manager can list domain trust user group delegates
      if their domain matches the delegate's domain ID on the domain trust.
    - Users with the role ``identity:domain-trust-admin`` can list user group
      delegates on any domain trust.

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

The following table shows the header and URI parameters for the request:

.. csv-table::
   :header: Name, Type, Description
   :widths: auto

    X-Auth-Token, String *(Required)*, A valid authentication token.
    {trustId}, URI String *(Required)*, A domain trust ID.

**Example: List domain trust user group delegates: JSON request**

.. code::

    GET /v2.0/RAX-AUTH/trusts/21345/delegates/user-groups
    Host: identity.api.rackspacecloud.com
    Accept: application/json
    Content-type: application/json
    X-Auth-Token: c6f56a1d89274da4b14c1de36c412345

This operation does not accept a request body.

--------
Response
--------

**Example: List a domain trust user group delegates JSON response**

.. code::

    HTTP/1.1 200 OK
    Content-Type: application/json

    {
        "user-groups": [
            "099b8893843441c3a74901bfd7e9131a",
            "099b8893843441c3a74901bfd7e9131b"
        ]
    }

