.. _auth-rbac-roles:

Role-based access control
~~~~~~~~~~~~~~~~~~~~~~~~~

.. contents::
   :local:
   :depth: 1

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

Assigning roles
---------------

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

-  :ref:`Add account user <post-add-user-v2.0-users>`

-  :ref:`Assign role to account users <add-role-to-user-v2.0-os-ksadm>`

-  :ref:`Delete role from account user <delete-global-role-from-user-v2.0-os-ksadm>`

For information about implementing RBAC by using the Cloud Control Panel
and other RBAC-related topics, see the following Rackspace Knowledge
Center articles:

- `Getting Started with role-based access control (RBAC)`_

- `Managing role-based access control through Cloud Control Panel`_


.. comments  Reference URLs

.. _Managing role-based access control through Cloud Control Panel: http://www.rackspace.com/knowledge_center/article/managing-role-based-access-control-rbac

.. _Getting Started with role-based access control (RBAC): http://www.rackspace.com/knowledge_center/article/getting-started-with-role-based-access-control-rbac-0


.. _auth-resolve-rbac-role-conflicts:

Resolving role conflicts between roles
--------------------------------------

The account owner can assign both multiproduct (global) roles and custom
(product-specific). In some cases, the scope of these roles can overlap and
cause conflict. When conflicts occur, the role that provides the more
extensive permissions takes precedence. Therefore, admin roles take precedence
over observer roles, because admin roles provide more permissions.

The following table shows two examples of how potential conflicts
between user role assignments are resolved:

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

For information about using RBAC with specific products, see
the :rax-devdocs:`API Developer Guide <>` for each product.
