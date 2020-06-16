.. _post-reset-api-key-for-user-v2.0:

Reset API key for user
~~~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /v2.0/users/{userId}/OS-KSADM/credentials/RAX-KSKEY:apiKeyCredentials/RAX-AUTH/reset

Use the Reset API Key operation to reset the API key on the specified user
account.

Identity users and user administrators should routinely reset passwords and API
keys  to prevent unauthorized access to Rackspace Cloud accounts and services.

This reset operation returns the new API key for the user account. Unlike
updating the password,  the API key reset does not revoke existing tokens.
Identity user administrators can  use the :ref:`Revoke Token
<delete-revoke-token-v2.0>` operation to invalidate the token for a user.

.. note::

  - Users can always use this service to reset the API key credentials for
    themselves.

  - Users with the ``identity:service-admin`` role can reset API key
    credentials for users with the ``identity:admin`` role, users with the
    ``identity:user-admin`` role, and sub-users.

  - Users with the ``identity:admin`` role can reset API key credentials for
    users with the ``identity:user-admin`` role and sub-users.

  - Users with the ``identity:user-admin`` and ``identity:user-manage`` role
    can reset API key credentials for users within their domain and with the
    ``identity:default`` role.

This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |The request succeeded.   |
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
|415                       |Bad Media Type           |Bad media type. This may |
|                          |                         |result if the wrong      |
|                          |                         |media type is used in    |
|                          |                         |the API request. Check   |
|                          |                         |the content-type and     |
|                          |                         |accept headers included  |
|                          |                         |in the request.          |
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
|{userId}                  |URI String               |A user ID assigned by    |
|                          |String *(Required)*      |system when user is      |
|                          |                         |added.                   |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.

Response
--------

**Example: Reset API key for user: XML response**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <apiKeyCredentials apiKey="aaaaa-bbbbb-ccccc-12345678"
        username="jqsmith"
        xmlns="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"
        xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
        xmlns:atom="http://www.w3.org/2005/Atom"
        xmlns:identity="http://docs.openstack.org/identity/api/v2.0"/>

**Example: Reset API key for user: JSON response**


.. code::

   {
     "RAX-KSKEY:apiKeyCredentials": {
       "username": "jqsmith",
       "apiKey": "aaaaa-bbbbb-ccccc-12345678"
     }
   }
