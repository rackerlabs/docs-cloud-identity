.. _get-list-effective-roles-assigned-to-a-user-v2.0:

List effective roles assigned to a user
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /v2.0/users/{userId}/RAX-AUTH/roles

This operation returns the list of all roles that are assigned to the user with
the specified user Id. If you don't know the user ID, use the
:ref:`Get user by Id <get-user-by-id-v2.0>` operation to find it.

For each role listed, the response includes identifying information such as the
role ID, name, and tenants to which the role is assigned, and the sources that
determined how the user received the role on the specified tenants.

This calls differs from the similar
:ref:`List global roles assigned to a user
<get-list-global-roles-assigned-to-a-user-v2.0>` call by:

- Including all means by which a user can be granted a role including:

  - Through the user itself
  - Through membership in a user group
  - Through the system

- Including all forms of role assignment

  - On domain
  - On individual tenants
  - On RCN

The :ref:`List global roles assigned to a user
<get-list-global-roles-assigned-to-a-user-v2.0>` accounts only for roles
assigned through the user on the domain.

.. note::

   - Users can always use this service to list roles for themselves.

   - Users with the ``identity:user-admin`` or ``identity:user-manage``
     role can list roles for users within their domain and with the
     ``identity:default`` role.

   - Use the service only to return roles for provisioned users.
     Returning roles for federated users is not yet supported.

.. csv-table::
   :header: Response code, Name, Description

   200, OK, The request has been fulfilled. The roles have been retrieved.
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

   X-Auth-Token, String *(Required)*, A valid authentication token.

This table shows the URI parameters for the request:

.. csv-table::
   :header: Name, Type, Description

   {userId}, String, The id of the user for which roles should be returned.

This table shows the query parameters for the request:

.. csv-table::
   :header: Name, Type, Description
   :widths: auto

   onTenantId, String *(Optional)*, "Filter roles that have been granted on
   the specified tenantId for the user."

This operation does not accept a request body.

**Example List global roles assigned to a user: XML request**

.. code::

   GET /v2.0/users/123456/RAX-AUTH/roles HTTP/1.1
   Host: identity.api.rackspacecloud.com
   X-Auth-Token: 771dd18634734a46b49f2af620112345
   Accept: application/xml
   Content-type: application/xml

**Example List global roles assigned to a user: JSON request**

.. code::

   GET /v2.0/users/123456/RAX-AUTH/roles HTTP/1.1
   Host: identity.api.rackspacecloud.com
   X-Auth-Token: 771dd18634734a46b49f2af620112345
   Accept: application/json
   Content-type: application/json

Response
--------

The response groups by role. Each role is shown as a ``tenantAssignment`` with
all tenants on which the user has the role included, regardless of the tenant's
domain.

.. list-table::
   :header-rows: 1
   :widths: 30 20 30

   * - Name
     - Type
     - Description
   * - **RAX-AUTH:roleAssignments**
     - Object *(Required)*
     - A role assignments entity.
   * - RAX-AUTH:roleAssignments.\ **tenantAssignments**
     - Object *(Required)*
     - An array of tenant assignments.
   * - RAX-AUTH:roleAssignments.tenantAssignments.\ **onRole**
     - String *(Required)*
     - Role ID for tenant assignment.
   * - RAX-AUTH:roleAssignments.tenantAssignments.\ **onRoleName**
     - String *(Required)*
     - Role name for tenant assignment.
   * - RAX-AUTH:roleAssignments.tenantAssignments.\ **forTenants**
     - String *(Required)*
     - An array of tenant IDs to which the role is assigned. This is the union
       of all tenants across all sources for the role
   * - RAX-AUTH:roleAssignments.tenantAssignments.\ **sources**
     - An array of sources *(Required)*
     - An array of sources which grant the user the role on the specified
       tenant(s)
   * - RAX-AUTH:roleAssignments.tenantAssignments.sources.\ **sourceType**
     - String *(Required)*
     - The source of the role assignment. This can be
        - USER
        - USERGROUP
        - SYSTEM
   * - RAX-AUTH:roleAssignments.tenantAssignments.sources.\ **sourceId**
     - String *(Required)*
     - A unique identifier for the source. For users and groups this is the
       respective id. For SYSTEM, this is the source system (e.g. IDENTITY)
   * - RAX-AUTH:roleAssignments.tenantAssignments.sources.\ **assignmentType**
     - String *(Required)*
     - How tenants are determined for the source. This can be one of
        - DOMAIN
        - TENANT
        - RCN
   * - RAX-AUTH:roleAssignments.tenantAssignments.sources.\ **forTenants**
     - Array of Strings *(Required)*
     - The list of tenants to which the source grants the user the role.

-------
Sources
-------
The response includes one or more sources for each role that the user has
assigned. Each source includes a source type, source id, assignment type, and
tenants on which that source granted the user the specified role.

SourceType and SourceId
^^^^^^^^^^^^^^^^^^^^^^^
A user can receive a given role through multiple methods.

.. list-table:: Source Type
   :header-rows: 1
   :widths: 20 60

   * - Type
     - Description
   * - USER
     - Direct role assignment to the user
   * - USERGROUP
     - Indirect assignment to the user via user groups
   * - SYSTEM
     - Identity System level functionality that automatically assigns certain
       roles

The ``sourceId`` identifies the id of the ``sourceType``. For example, the
``sourceId`` for the source with a ``USER`` source type is the ID for the
user to which the role was directly assigned, whereas the ``sourceId`` for a
``USERGROUP`` type would be the ID for the user group.

Assignment type
^^^^^^^^^^^^^^^
Role assignments are classified in to three ways based on how the tenants for
which those assignments apply are determined.

.. list-table:: Source type
   :header-rows: 1
   :widths: 20 60

   * - Type
     - Description
   * - DOMAIN
     - Assignment applied to all tenants within the user's domain.
   * - TENANT
     - Assignment only applies to tenants to which the role was explicitly
       assigned.
   * - RCN
     - Applies to all tenants across all domains within the RCN for which the
       RCN role applies.

--------
Examples
--------
**Generic Example Response**

This example is contrived to show the different ``sourceTypes`` in a single
example, and is not meant to represent an real world example.

JSON::

 {
    "RAX-AUTH:roleAssignments": {
        "tenantAssignments": [
            {
                "onRole": "1234",
                "onRoleName": "roleName",
                 "forTenants": [
                     "t1",
                     "t2"
                 ],
                "sources": [
                  {
                       "sourceType": "USER",
                       "sourceId": "userId",
                       "assignmentType": "DOMAIN"
                       "forTenants": [
                          "t1",
                          "t2"
                       ]
                  },
                  {
                       "sourceType": "USERGROUP",
                       "sourceId": "UserGroupAId",
                       "assignmentType": "DOMAIN",
                       "forTenants": [
                          "t1",
                          "t2"
                       ]
                  },
                  {
                       "sourceType": "USERGROUP",
                       "sourceId": "UserGroupBId",
                       "assignmentType": "TENANT",
                       "forTenants": [
                          "t1",
                          "t2"
                       ]
                  },
                  {
                       "sourceType": "USERGROUP",
                       "sourceId": "UserGroupCId",
                       "assignmentType": "TENANT",
                       "forTenants": [
                          "t1"
                       ]
                  },
                  {
                       "sourceType": "SYSTEM",
                       "sourceId": "IDENTITY",
                       "assignmentType": "TENANT",
                       "forTenants": [
                          "t2"
                       ]
                  }
                ]
            }
        ]
    }
 }

**Across Domains Assignment Example Response**

Assume:

- d1t1 and d1t2 are tenants within the same domain (Domain 1).
- d2t1 is a tenant in a different domain (Domain 2).
- The user has the 'observer' role assigned on tenant d1t1, d1t2 in Domain 1
  and on tenant d2t1 on Domain 2.

JSON::

 {
    "RAX-AUTH:roleAssignments": {
        "tenantAssignments": [
            {
                "onRole": "8899",
                "onRoleName": "observer",
                "forTenants": [
                     "d1t1",
                     "d1t2",
                     "d2t1"
                 ],
                "sources": [
                  {
                       "sourceType": "USER",
                       "sourceId": "userId",
                       "assignmentType": "DOMAIN",
                       "forTenants": [
                         "d1t1",
                         "d1t2",
                         "d2t1"
                     ]
                  }
                ]
            }
        ]
    }
 }

**RCN Role Example Response**

Assume:

- The user's RCN contains the domain Domain 1 with the d1t1 and d1t2 tenants.
- The user's RCN contains the domain Domain 2 with the d2t1 tenants.
- The RCN role applies to all the mentioned tenants.


JSON::

 {
    "RAX-AUTH:roleAssignments": {
        "tenantAssignments": [
            {
                "onRole": "8899",
                "onRoleName": "rcn:admin",
                "forTenants": [
                   "d1t1",
                   "d1t2",
                   "d2t1"
                ],
                "sources": [
                   {
                      "sourceType": "USER",
                      "sourceId": "userId",
                      "assignmentType": "RCN"
                      "forTenants": [
                         "d1t1",
                         "d1t2",
                         "d2t1"
                      ]
                   }
                ]
            }
        ]
    }
 }

**User without Tenants Example Response**

A user could be assigned a role that doesn't apply to *any* current tenants for
the user. For example, the user may have only DOMAIN roles on a domain with no
tenants. The user could also be assigned an RCN role that doesn't match any
tenant within the user's RCN. The service returns the role, but shows that that
source doesn't apply to any tenants.

Assume:

- The user's domain does not contain any tenants
- The user has the identity:user-admin role

JSON::

 {
    "RAX-AUTH:roleAssignments": {
        "tenantAssignments": [
            {
                "onRole": "3",
                "onRoleName": "identity:user-admin",
                "forTenants": [],
                "sources": [
                  {
                       "sourceType": "USER",
                       "sourceId": "userId",
                       "assignmentType": "DOMAIN"
                       "forTenants": []
                  }
                ]
            }
        ]
    }
 }
