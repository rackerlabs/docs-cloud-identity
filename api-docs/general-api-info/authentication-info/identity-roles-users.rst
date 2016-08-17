.. _roles-and-role-assignments: 

Identity roles and users
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

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
   :ref:`role operations <roles-operations>` available through the Identity
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

