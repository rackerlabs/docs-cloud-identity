.. _get-list-domain-trust-roles:

List domain trust roles
~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /v2.0/RAX-AUTH/trusts/{trustId}/roles

List domain trust roles.

.. note::

    - A user-admin and user-manager can list a trust role if their domain
      matches the principal domain or delegate domain on the trust.
    - Users with the role ``identity:domain-trust-admin`` can list domain
      trusts roles for any principal and delegate domain.
    - Use the RAX-AUTH API extension to the Core Identity API to implement this
      API operation.

The following table shows the possible response codes for this operation:

.. csv-table::
  :header: Response Code, Name, Description
  :widths: 2, 2, 2

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
  :widths: 2, 2, 2

  X-Auth-Token, Header String *(Required)*, A valid authentication token for a user.
  {trustId}, URI String *(Required)*, A domain trust ID.

**Example: List domain trusts roles: JSON request**

.. code::

    GET /v2.0/RAX-AUTH/trusts/123456/roles
    Host: identity.api.rackspacecloud.com
    Accept: application/json
    Content-type: application/json
    X-Auth-Token: c6f56a1d89274da4b14c1de36c412345

--------
Response
--------

The following table shows the body parameters for the response:

.. csv-table::
  :header: Name, Type, Description
  :widths: 2, 2, 2

  **roleAssignments**, String *(Required)*, An object containing a list of role assignments.
  roleAssignments.\ **roles**, String *(Required)*, A list of roles that can be assigned to a delegate.

  **Example: List domain trusts roles: JSON response**

.. code::

    {
        "roleAssignments": [
            {
                "roles": [
                    "ticketing:observer",
                    "ticketing:admin"
                ]
            }
        ]
    }
