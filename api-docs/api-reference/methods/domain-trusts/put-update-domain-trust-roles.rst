.. _put-update-domain-trust-roles:

Update domain trust roles
~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    PUT /v2.0/RAX-AUTH/trusts/{trustId}/roles

Update domain trust roles.

.. note::

    - A user-admin and user-manager can update a trust role if their domain
      matches the principal domain on the trust.
    - Users with the role ``identity:domain-trust-admin`` can update domain
      trusts role for any principal and delegate domain.
    - Use the RAX-AUTH API extension to the Core Identity API to implement this
      API operation.

The following table shows the possible response codes for this operation:

.. csv-table::
  :header: Response Code, Name, Description
  :widths: 2, 2, 2

  200, OK, The request has been fulfilled. The domain trust has been updated.
  400, Bad Request, The request was invalid.
  401, Unauthorized, You are not authorized to complete this operation. This error can occur if the request is submitted with an invalid authentication token.
  403, Forbidden, Caller does not have an appropriate role.
  405, Invalid Method, The method specified in the request is not valid for the resource identified in the request URI.
  409, Conflict, A domain trust already exists for the given delegate and principal domains.
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

The following table shows the body parameters for the request:

.. csv-table::
  :header: Name, Type, Description
  :widths: 2, 2, 2

  **roleAssignments**, String *(Required)*, An object containing a list of role assignments.
  roleAssignments.\ **roles**, String *(Required)*, A list of roles that can be assigned to a delegate.

**Example: Granting roles to a domain trust JSON Request**

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

--------
Response
--------

The following table shows the body parameters for the response:

.. csv-table::
  :header: Name, Type, Description
  :widths: 2, 2, 2

  **roleAssignments**, String *(Required)*, An object containing a list of role assignments.
  roleAssignments.\ **roles**, String *(Required)*, A list of roles that can be assigned to a delegate.

**Example: Granting roles to a domain trust JSON Response**

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
