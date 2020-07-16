.. _get-domain-trust-user-delegate-roles:

Get domain trust user delegate roles
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /v2.0/RAX-AUTH/trusts/{trustId}/delegates/users/{userId}/roles

Get domain trust user delegate roles.

.. note::

    - A user-admin and user-manager can get the roles for a user delegate
      if their domain matches the domain of the user.
    - Users with the role ``identity:domain-trust-admin`` can get roles
      for any user delegate.

The following table shows the possible response codes for this operation:

.. csv-table::
  :header: Response Code, Name, Description
  :widths: 2, 2, 2

  200, OK, The request has been fulfilled.
  400, Bad Request, The request was invalid.
  401, Unauthorized, You are not authorized to complete this operation. This error can occur if the request is submitted with an invalid authentication token.
  403, Forbidden, Caller does not have an appropriate role.
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
  {userId}, URI String *(Required)*, The user ID for the domain trust delegate.


This operation does not accept a request body.

--------
Response
--------

**Example: Get roles to a user delegate JSON Response**

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
