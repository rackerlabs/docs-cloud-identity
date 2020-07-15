.. _put-update-domain-trust-user-group-delegate-roles:

Update domain trust user group delegate roles
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    PUT /v2.0/RAX-AUTH/trusts/{trustId}/delegates/user-groups/{userGroupId}/roles

Update domain trust user group delegate roles.

.. note::

    - A user-admin and user-manager can update the roles for a user group delegate
      for any user group in their domain.
    - Users with the role ``identity:domain-trust-admin`` can update roles
      for any user group delegate.
    - Roles can be delegated to a user only if they are part of the domain
      trust roles assignment.

The following table shows the possible response codes for this operation:

.. csv-table::
  :header: Response Code, Name, Description
  :widths: 2, 2, 2

  200, OK, The request has been fulfilled. The roles have been updated.
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
  {userGroupId}, URI String *(Required)*, The user group ID for the domain trust delegate.

The following table shows the body parameters for the request:

.. csv-table::
  :header: Name, Type, Description
  :widths: 2, 2, 2

  **roleAssignments**, String *(Required)*, "An object containing a list of role assignments."
  roleAssignments.\ **roles**, String *(Required)*, "A list of roles that are delegated to the user."
  roleAssignments.\ **conditions**, String *(Required)*, "A list of conditions defining how the role is applied. The conditions are provided in the format ``id=<tenantId>``"
  roleAssignments.\ **resourceType**, String *(Required)*, "The type of resource that the role is applied to. Valid values are ``domain`` or ``tenant``."

**Example: Granting roles to a user group delegate JSON Request**

.. code::

    {
        "roleAssignments": [
            {
                "conditions": [
                    "id=faws:123"
                ],
               "resourceType": "tenant",
               "roles": [
                   "observer"
               ]
            },
            {
                "conditions": [
                    "id=faws:123"
                ],
                "resourceType": "tenant",
                "roles": [
                    "ticketing:observer"
                ]
            },
            {
                "resourceType": "domain",
                "roles": [
                    "ticketing:admin"
                ]
            }
        ]
    }

--------
Response
--------

**Example: Granting roles to a user group delegate JSON Response**

.. code::

    {
        "roleAssignments": [
            {
                "conditions": [
                    "id=faws:123"
                ],
               "resourceType": "tenant",
               "roles": [
                   "observer"
               ]
            },
            {
                "conditions": [
                    "id=faws:123"
                ],
                "resourceType": "tenant",
                "roles": [
                    "ticketing:observer"
                ]
            },
            {
                "resourceType": "domain",
                "roles": [
                    "ticketing:admin"
                ]
            }
        ]
    }
