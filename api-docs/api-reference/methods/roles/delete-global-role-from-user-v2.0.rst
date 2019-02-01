.. _delete-global-role-from-user-v2.0-os-ksadm:

Delete global role from user
~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.. code::

    DELETE /v2.0/users/{userId}/roles/OS-KSADM/{roleid}

Use this operation to delete a multi-product or custom (product-specific) role
from a  user account.

When you submit the request, include the system-assigned role ``id`` and user
``id``  in the request. Use the List role and List user operations to find the
correct ids.

The DELETE operation allows the account owner (identity:user-admin) to manage
non-protected role assignment for users (identity:default), granting and
revoking  access at will. Some roles like identity:rack_connect and
identity:rax_managed  cannot be managed by customers to prevent them from
revoking privileges unintentionally.

.. note::

  - Users with the ``identity:service-admin`` role can delete a global role
    from a user for users with the ``identity:admin`` role, users with the
    ``identity:user-admin`` role, and sub-users.

  - Users with the ``identity:admin`` role can delete a global role from a user
    for users with the ``identity:user-admin`` role, and sub-users.

  - Users with the ``identity:user-admin`` or ``identity:user-manage`` role can
    delete a global role from sub-users within their domain that have the
    ``identity:default`` role.

This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|204                       |No content               |The request succeeded.   |
|                          |                         |The server fulfilled the |
|                          |                         |request but does not     |
|                          |                         |need to return a body.   |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |The request is missing   |
|                          |                         |one or more elements, or |
|                          |                         |the values of some       |
|                          |                         |elements are invalid.    |
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |You are not authorized   |
|                          |                         |to complete this         |
|                          |                         |operation. This error    |
|                          |                         |can occur if the request |
|                          |                         |is submitted with an     |
|                          |                         |invalid authentication   |
|                          |                         |token.                   |
+--------------------------+-------------------------+-------------------------+
|403                       |Forbidden                |The request was valid,   |
|                          |                         |but the server is        |
|                          |                         |refusing to respond      |
|                          |                         |because you do not have  |
|                          |                         |permission to access the |
|                          |                         |requested resource.      |
|                          |                         |Submit a request to your |
|                          |                         |account administrator to |
|                          |                         |determine how to gain    |
|                          |                         |access.                  |
+--------------------------+-------------------------+-------------------------+
|404                       |Not Found                |The requested resource   |
|                          |                         |was not found.           |
+--------------------------+-------------------------+-------------------------+
|405                       |Invalid Method           |The method specified in  |
|                          |                         |the request is not valid |
|                          |                         |for the resource         |
|                          |                         |identified in the        |
|                          |                         |request URI.             |
+--------------------------+-------------------------+-------------------------+
|413                       |Over Limit               |The number of items      |
|                          |                         |returned is above the    |
|                          |                         |allowed limit.           |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Fault            |Service is not available.|
+--------------------------+-------------------------+-------------------------+


Request
-------

This table shows the header and URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|X-Auth-Token              |Header                   |A valid admin            |
|                          |String *(Required)*      |authentication token.    |
+--------------------------+-------------------------+-------------------------+
|{userId}                  |URI                      |A user ID assigned by    |
|                          |String *(Required)*      |system when user is      |
|                          |                         |added.                   |
+--------------------------+-------------------------+-------------------------+
|{roleId}                  |String *(Required)*      |A role Id.               |
+--------------------------+-------------------------+-------------------------+


This operation does not accept a request body.

**Example Delete global role from user: XML request**


.. code::

   DELETE /v2.0/users/123456/roles/OS-KSADM/30007896 HTTP/1.1
   Host: identity.api.rackspacecloud.com
   X-Auth-Token:82994d2fb9a0483a85b6ba622c212345
   Accept: application/xml
   Content-type: application/xml


**Example Delete global role from user: JSON request**


.. code::

   DELETE /v2.0/users/123456/roles/OS-KSADM/30007896 HTTP/1.1
   Host: identity.api.rackspacecloud.com
   X-Auth-Token:82994d2fb9a0483a85b6ba622c212345
   Accept: application/json
   Content-type: application/json


Response
--------

This operation does not return a response body.
