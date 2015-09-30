.. _auth-resp-user-resource:

User resource: authentication response attributes
..............................................................

The user object returns account information for the authenticated user
that includes user name, ID, default region assignment, and information
about role assignments.

Users can have multiple roles, with each role providing specific
privileges. For example, each account has an `Identity
role <auth-rbac-roles>`
such as `Identity:default` to authenticate and gain access to Identity
service capabilities and any other RBAC roles assigned to the
account.

Responses can be in :ref:`JSON <auth-resp-example-user-resp-json>` or
:ref:`XML <auth-resp-example-user-resp-xml>`. For details, see
the `user object attribute descriptions <auth-resp-user-obj-attribs>` in
the table following the examples.


.. _auth-resp-example-user-resp-json:

**Example: Authentication response: User object in JSON format**

.. code::  

      "user": {
                "id": "172157",
                "roles": [
                    {
                        "id": "10000150",
                        "description": "Checkmate Access role",
                        "name": "checkmate"
                    },
                    {
                        "tenantId": "MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f",
                        "id": "5",
                        "description": "A Role that allows a user access to keystone Service methods",
                        "name": "object-store:default"
                    },
                    {
                        "tenantId": "123456",
                        "id": "6",
                        "description": "A Role that allows a user access to keystone Service methods",
                        "name": "compute:default"
                    },
                    {
                        "id": "3",
                        "description": "User Admin Role.",
                        "name": "identity:user-admin"
                    }
                ],
                "name": "yourUserName",
                "RAX-AUTH:defaultRegion": "DFW"
            }


.. _auth-resp-example-user-resp-xml: 
 
**Example: Authentication response: User object in XML format**

.. code::  

    <user id="187345" name="yourUserName" rax-auth:defaultRegion="DFW">
        <roles>
            <role id="10000150" name="checkmate" description="Checkmate Access role" rax-auth:propagate="false"/>
            <role id="5" name="object-store:default" description="A Role that allows a user access to keystone Service methods" 
                    tenantId="MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f" rax-auth:propagate="true"/>
            <role id="6" name="compute:default" description="A Role that allows a user access to keystone Service methods" 
                    tenantId="123456" rax-auth:propagate="true"/>
            <role id="3" name="identity:user-admin" description="User Admin Role." rax-auth:propagate="false"/>
            </roles>
        </user>
       

.. _auth-resp-user-obj-attribs:

The user object returns user information and a roles object that listes the roles 
associated with the user account.                              

**Table: The user object attributes**

+-------------------------+--------+-----------------------------------------------------+
| Attribute               | Type   | Description                                         |
+=========================+========+=====================================================+
| `id`                    | String |The unique, system-generated ID assigned to the      |
|                         |        |user account. The user ID is required by many API    |
|                         |        |operations for managing user accounts and            |
|                         |        |information.                                         |
+-------------------------+--------+-----------------------------------------------------+
| `name`                  | String | The name assigned to the user account.              |
+-------------------------+--------+-----------------------------------------------------+
|`RAX-AUTH:defaultRegion` | String | If API requests to a Rackspace Cloud service do not |
|                         |        | explicitly specify a region and multiple endpoints  |
|                         |        | are available, the RAX-AUTH:defaultRegion determines|
|                         |        | the region that is selected by default. Use the     |
|                         |        | update user API operation to change the value.      |
|                         |        | change the value.                                   |
+-------------------------+--------+-----------------------------------------------------+



**Table: The roles object attributes** 

+---------------+--------+----------------------------------------------------------------+
| Attribute     | Type   | Description                                                    |
+===============+========+================================================================+
| `id`          | String | The unique, system-generated ID assigned to the role in the    |
|               |        | Identity system.                                               |
+---------------+--------+----------------------------------------------------------------+
| `name`        | String | The name that identifies the role in the Identity system.      |
+---------------+--------+----------------------------------------------------------------+
| `description` | String | Provides information about the role and its intended use.      |
+---------------+--------+----------------------------------------------------------------+
| `tenantID`    | String | Identifies the tenant for which the role is scoped.            |
+---------------+--------+----------------------------------------------------------------+
