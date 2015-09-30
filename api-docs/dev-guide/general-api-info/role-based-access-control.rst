.. _auth-roles-and-assignments: 

Roles and role assignments
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The Identity service provides different role types to simplify the
access control configuration and management for Rackspace Cloud tenant
and user accounts.

-  :ref:`Service-managed roles <auth-roles-svc-adm-usr>` 
   allow Service and Identity administrators to restrict access to
   services and capabilities within a service. These roles can only be
   assigned to customers by Service or Identity administrators. Service
   Managed roles must be created by Identity operations staff in the
   Identity service configuration. You cannot create them through the
   Identity service API.

   Service managed roles can be configured with the propagate attribute.
   When this attribute is set, roles held by Identity administrators and
   User managers are inherited automatically by all user accounts that
   the administrator creates and manages.

-  The :ref:`Role-based access control (RBAC) roles <auth-roles-svc-adm-usr>` 
   feature allows customers to create, manage, and assign roles to restrict access to Cloud services
   and capabilities to authorized users only. RBAC is an opt-in feature
   available to all customers. Account owners can activate RBAC by
   adding users to the account and assigning roles to users via the API,
   the Cloud Control Panel, or by calling Customer support.

   Administrators and customers with sufficient access rights can
   create, manage, and assign RBAC roles by using the 
   :ref:`role operations <role-operations>` available through the Identity
   service API.

Roles can be configured with a global or product-specific scope.

-  Global roles such as admin and observer are effective for all
   products with the exception of the Identity service. The Identity
   service does not use global roles to make access control decisions
   within the Identity service.

-  Product roles are effective for a specific product and are linked to
   the product through the role name. For example, the dnsaas:admin is
   the administrator role for the DNS service, and Lbaas:observer is the
   observer role for the Load Balancers service. Product roles are also
   called custom roles.


.. _auth-roles-svc-adm-usr:

Identity service, admin, and user roles
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Identity roles are service managed roles defined and managed by
Rackspacee that the Identity service uses to make access control
decsions when a user or service submits an API request to the Identity
API.

In the Rackspace Cloud, users are represented as accounts created for
associated with the account. When a user is created, the Identity
service automatically assigns a default Identity role to the account,
based on the Identity service system configuration. The Identity role
defines the access rights and permissions for using the Identity service
as shown in the following table.

.. _auth-tbl-svc-account-user-type-roles:

**Table:  Identity service Accounts: User types and default role assignments**

+---------------+-----------------+-------------------------------------------------+
| Role name     | Account user    | Description                                     |
|               | type            |                                                 |
+===============+=================+=================================================+
|`identity:`    | Service         | A Rackspace-restricted role that provides full  |
|`service-admin`| administrator   | administrative rights and privileges to manage  |
|               |                 | the Identity service. This role is assigned     |
|               |                 | only to Cloud Identity Operations team member   |
|               |                 | accounts.                                       |
+---------------+-----------------+-------------------------------------------------+
| `identity:`   | Identity        | A Service role that allows Rackspace Cloud      |
| `admin`       | administrator   | Services like Cloud Servers and Cloud Load      |
|               |                 | Balancers to access the Identity service to     |
|               |                 | validate tokens and retrieve user information.  |
+---------------+-----------------+-------------------------------------------------+
| `identity:`   | Identity User   | A customer role that is assigned automatically  |
| `user-admin`  | Administrator   | when a user creates a Rackspace Cloud account.  |
|               | also known as   | The `identity:user-admin` provides full         |
|               | the Account     | administrative privileges to manage the primary |
|               | owner           | account and all user accounts created within    |
|               |                 | the account.                                    |
|               |                 |                                                 |
|               |                 | Each Rackspace Cloud account has exactly one    |
|               |                 | administrative user. This user is also referred |
|               |                 | to as the Account Owner or User Administrator.  |
+---------------+-----------------+-------------------------------------------------+
| `identity:`   | Identity User   | A customer role that provides the same access   |
| `user-manage` | Manager         | rights and privleges as the                     |
|               |                 | `identity:user-admin` role.                     |
|               |                 |                                                 |
|               |                 | A Rackspace Cloud User Administrator can grant  |
|               |                 | administrative privileges to a user that holds  |
|               |                 | the `identity:default` role by assigning the    |
|               |                 | `identity:user-manage` role to that account.    |
+---------------+-----------------+-------------------------------------------------+
| `identity:`   | Identity        | A customer role that is assigned automatically  |
| `default`     | sub-user        | to user accounts that a User Administrator or   |
|               |                 | User Manager creates within a Rackspace Cloud   |
|               | Account user    | account.                                        |
|               |                 |                                                 |
|               |                 | The `identity:default` role provides users      |
|               |                 | with the rights and privileges to manage their  |
|               |                 | own account. For example, account users can     |
|               |                 | update user information and passwords on their  |
|               |                 | own accounts, but they cannot update            |
|               |                 | information on other accounts. A user with the  |
|               |                 | `identity:default` role can submit a List       |
|               |                 | users request, but the response only returns    |
|               |                 | information about the account owner.            |
+---------------+-----------------+-------------------------------------------------+


Typically, a user account has only one Identity role that is assigned when the account 
is created or updated. However, if the User Administrator updates a sub-user account 
to add the `identity:user-manage` role the account has two Identity roles:
`identity:default` and `identity:user-manage`.

The account owner user (`identity:user-admin`) can activate RBAC by adding users to 
the account and assigning roles to users via the API, the Cloud Control Panel, or 
by calling Customer support. An account can have additional customer-managed RBAC 
product or global roles assigned to manage access and permissions for other Rackspace 
services. For details, see :ref:`Rackspace Cloud RBAC Roles and
Capabilities <auth-tbl-rbac-roles-and-capabilities>`.

Usage notes
............. 

When managing Rackspace Cloud accounts as the User Administrator, keep the following points in mind to prevent unexpected changes to the
sub-user accounts associated with the User administrator account.

-  When a new account user is created, the account inherits the tenant
   information, group memberships. amd endpoints from the User
   administrator account.

-  If the User administrator account is assigned to a new group, its
   account users are also added to the group.

-  If a User administrator account is removed from a group, the account
   users are also removed.

- If a service attempts to assign an account user to a group, the
  attempt fails with the following error message: 

    ``400  Cannot add sub-users directly to a group, must assign their parent user.`` 
          
  Correct the problem by assigning the User administrator parent account to
  the group so that the account user inherits the assignment.

- Administrators can directly assign account users to a particular tenant so that the 
  users behave as if they are contained within that tenant.


.. _auth-rbac-roles:

RBAC roles
^^^^^^^^^^

RBAC roles are cusotmer-managed roles with specific permissions that
determine the services a user can access and the types of operations
they can complete. For example, an account user with the `lbaas:admin`
role has create, read, update, and delete permissions for the Cloud
Loadbalancer service.

All RBAC roles are subordinate to the `identity:user-admin` or the
`identity:user-manage` roles that the Identity service assigns to
Rackspace Cloud accounts held by the account owner or by an account
designated to manage user accounts. Only Identity administrators and
managers can create account users (`identity:default`) and assign RBAC
roles. Account owners cannot hold any additional roles because they
already have full access to all services and capabilities. Account
managers can have both the `identity:user-manage` and the
`identity:default`.

Role assignments can be global or custom. Global roles manage access and
permissions across multiple API services. Custom roles manage access and
permissions on a per-product basis. For both global and custom roles,
the user has access only to designated products. The following table 
describes the RBAC roles available.

.. _auth-tbl-rbac-roles-and-capabilities:

**Table: Rackspace Cloud RBAC Roles and Capabilities**

+---------------------+--------+----------------------------------------------+------------+
| Role                | Type   | Role Description                             | Example    |
|                     |        |                                              | Role       |
+=====================+========+==============================================+============+
| admin (full access) | Global | The admin role provides Create, read, update,|  Admin     |
|                     |        | and delete permissions in all Cloud products,|            |
|                     |        | where access is granted. Full access is given|            |
|                     |        | to current and future products as they become|            |
|                     |        | RBAC-enabled. Each account can have only one |            |
|                     |        | admin user.                                  |            |                      
+---------------------+--------+----------------------------------------------+------------+
| observer            | Global | The observer role provides read permission in| observer   |
| (read-only access)  |        | all products where access is granted.        |            |
|                     |        | Read-only access is given to current and     |            |
|                     |        | future products as they become RBAC-enabled. |            |
+---------------------+--------+----------------------------------------------+------------+
| product:admin       | Custom | The product:admin role provides create,      | nova:      |
|                     |        | read, update, and delete permissions for a   | admin      |
|                     |        | specified product, where access is granted.  |            |                                                                                                    
+---------------------+--------+----------------------------------------------+------------+
| product:creator     | Custom | The product:creator role provides create,    |cloudFiles: | 
|                     |        | read, and update permissions for a specified |creator     |
|                     |        | product, where access is granted. The user   |            |
|                     |        | cannot delete resources.                     |            |
+---------------------+--------+----------------------------------------------+------------+
| product:observer    | Custom | This product:observer role provides Read     | cdb:       |
|                     |        | permission for a specified product, where    | observer   |
|                     |        | access is granted.                           |            |
+---------------------+--------+----------------------------------------------+------------+



.. _auth-assign-roles-users:

Assigning roles to account users
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
The account owner, ``identity:user-admin`` can create account users,
``identity:default`` on the account and then assign roles to those
users. The roles grant the account users specific permissions for
accessing the Cloud services and capabilities. Each account has only one
account owner, and that role is assigned by default to any Rackspace
Cloud account when the account is created. Account owners cannot hold
any additional roles because they already have full access to all
services and capabilities.

You can assign roles programmatically through the API or by using the
Cloud Control panel interface.

Use the following API operations to add account users and manage role
assignments:

-  `Add account user`_

-  `Assign role to account users`_

-  `Delete role from account user`_

For information about implementing RBAC by using the Cloud Control Panel
and other RBAC-related topics, see the following Rackspace Knowledge
Center articles:

- `Getting Started with role-based access control (RBAC)`_

- `Managing role-based access control through Cloud Control Panel`_


.. comments  Reference URLs

.. _Add account user: http://docs.rackspace.com/auth/api/v2.0/auth-client-devguide/content/POST_addUser_v2.0_users_User_Calls.html

.. _Assign role to account users: http://docs.rackspace.com/auth/api/v2.0/auth-client-devguide/content/PUT_addUserRole__v2.0_users__userId__roles_OS-KSADM__roleid__Role_Calls.html

.. _Delete role from account user: http://docs.rackspace.com/auth/api/v2.0/auth-client-devguide/content/DELETE_deleteUserRole__v2.0_users__userId__roles_OS-KSADM__roleid__Role_Calls.html

.. _Managing role-based access control through Cloud Control Panel: http://www.rackspace.com/knowledge_center/article/managing-role-based-access-control-rbac

.. _Getting Started with role-based access control (RBAC): http://www.rackspace.com/knowledge_center/article/getting-started-with-role-based-access-control-rbac-0


.. _auth-resolve-rbac-role-conflicts:

Resolving Conflicts Between RBAC Multiproduct (Global) vs. Custom (Product) Roles
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The account owner can set roles for both multiproduct and custom
(product-specific) scope, and it is important to understand how any
potential conflicts among these roles are resolved. When two roles
appear to conflict, the role that provides the more extensive
permissions takes precedence. Therefore, admin roles take precedence
over observer roles, because admin roles provide more permissions.

The following table shows two examples of how potential conflicts
between user roles in the Control Panel are resolved:

+---------------------------------+---------------------------+---------------------------+
| Permission                      | View of permission        | Can the user perform      |
| configuration                   | in control panel          | product Admin functions   |
|                                 |                           | in the control panel?     |
+=================================+===========================+===========================+
| User is assigned the following  | Appears that the user     | Yes, for specified product|
| roles: multiproduct *observer*  | has only the multiproduct | product only. The user    |
| and product *admin*             | *observer* role           | has the *observer* role   |
|                                 |                           | for the rest of the       |
|                                 |                           | products.                 |
+---------------------------------+---------------------------+---------------------------+
| User is assigned the following  | Appears that the user has | Yes, for all of the       |
| roles: multiproduct *admin*     | only the multiproduct     | products. The specified   |
| and product *observer*          | *admin* role.             | product *observer* role   | 
|                                 |                           | is ignored.               |
+---------------------------------+---------------------------+---------------------------+

For information about using RBAC with specific products, see the `API
Developer Guide`_.

.. _API Developer Guide: http://docs.rackspace.com/