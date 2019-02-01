.. _put-grant-roles-to-user-v2.0:

Grant roles to a user
~~~~~~~~~~~~~~~~~~~~~

.. code::

   PUT /v2.0/users/{userId}/RAX-AUTH/roles

Grant roles to a provisioned user. Existing roles set on the user that are not
being modified remain unchanged.

.. note::

  - Users with the ``identity:service-admin`` role can grant roles to a user
    for users with the ``identity:admin`` role, users with the
    ``identity:user-admin`` role, and sub-users.

  - Users with the ``identity:admin`` role can grant roles to a user for users
    with the ``identity:user-admin`` role and sub-users.

  - Users with the ``identity:user-admin`` or ``identity:user-manage``
    role can grant roles to a user for users within their domain and with the
    ``identity:default`` role.

  - The caller must have at least the ``identity:user-manage`` role. If the
    caller has only domain access, verify that the caller's domain matches
    the target user's domain.

  - The tenants on assignments must belong to the same domain as the target
    user's domain.

  - The role assignments cannot assign identity user type roles with the
    exception of ``identity:user-manage``.

  - The caller must be authorized to assign the specified roles.

  - The tenant assignments can include either ["*"] or a set of tenant ids.

  - This request effectively replaces any assignment that already exists for
    these roles on the user.

This table shows the possible response codes for this operation:

.. csv-table::
   :header: Response code, Name, Description
   :widths: 15 25 60

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
   :widths: 25 25 50

   X-Auth-Token, String *(Required)*, A valid authentication token.

This table shows the URI parameters for the request:

.. csv-table::
   :header: Name, Type, Description
   :widths: 25 25 50

   {userId}, String, A user ID.

This table shows the body parameters for the request:

.. csv-table::
   :header: Name, Type, Description
   :widths: 25 25 50

    **RAX-AUTH:roleAssignments**, Object *(Required)*, A role assignments entity.
    RAX-AUTH:roleAssignments.\ **tenantAssignments** , Object *(Required)*, An array of tenant assignments.
    RAX-AUTH:roleAssignments.tenantAssignments.\ **onRole** , String *(Required)*, Role ID for tenant assignment.
    RAX-AUTH:roleAssignments.tenantAssignments.\ **forTenants** , Object *(Required)*, An array of tenant IDs. Use ["*"] for global tenant assignment.

**Example: Grant roles to a user request: XML**

.. code::

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <rax-auth:roleAssignments
        xmlns="http://docs.openstack.org/identity/api/v2.0"
        xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0">
         <rax-auth:tenantAssignments>
            <rax-auth:tenantAssignment forTenants="t1 t2" onRole="1234"/>
        </rax-auth:tenantAssignments>
    </rax-auth:roleAssignments>

**Example: Grant roles to a user request: JSON**

.. code::

    {
        "RAX-AUTH:roleAssignments": {
            "tenantAssignments": [
                {
                    "onRole": "1234",
                     "forTenants": [
                         "t1",
                         "t2"
                     ]
                }
            ]
        }
    }

Response
--------

**Example: Grant roles to a user response: XML**

.. code::

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <rax-auth:roleAssignments
        xmlns="http://docs.openstack.org/identity/api/v2.0"
        xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0">
         <rax-auth:tenantAssignments>
            <rax-auth:tenantAssignment forTenants="*" onRoleName="identity:user-admin" onRole="3"/>
            <rax-auth:tenantAssignment forTenants="t1 t2" onRoleName="roleName" onRole="1234"/>
        </rax-auth:tenantAssignments>
    </rax-auth:roleAssignments>

**Example: Grant roles to a user response: JSON**

.. code::

    {
        "RAX-AUTH:roleAssignments": {
            "tenantAssignments": [
                {
                    "onRole": "3",
                    "onRoleName": "identity:user-admin"
                    "forTenants": [
                        "*"
                    ],
                },
                {
                    "onRole": "1234",
                    "onRoleName": "roleName",
                     "forTenants": [
                         "t1",
                         "t2"
                     ]
                }
            ]
        }
    }
