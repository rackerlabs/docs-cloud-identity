
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-get-users-with-role-v2.0-os-ksadm-roles-roleid-rax-auth-users:

Get users with role
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v2.0/OS-KSADM/roles/{roleId}/RAX-AUTH/users

Gets users who have the specified role.

This operation does not require a request body.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |Request completed        |
|                          |                         |successfully.            |
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
""""""""""""""""




This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|X-Auth-Token              |String *(Required)*      |You need a valid admin   |
|                          |                         |token for access.        |
+--------------------------+-------------------------+-------------------------+
|{id}                      |String                   |The role ID.             |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




**Example Get users with role: XML request**


.. code::

   GET /v2.0/OS-KSADM/roles/10000209/RAX-AUTH/users HTTP/1.1
   Host: identity.api.rackspacecloud.com
   X-Auth-Token: 348052a0395e4d05929ef41685312345
   Accept: application/xml
   Content-type: application/xml





**Example Get users with role: JSON request**


.. code::

   GET /v2.0/OS-KSADM/roles/10000209/RAX-AUTH/users HTTP/1.1
   Host: identity.api.rackspacecloud.com
   X-Auth-Token: 348052a0395e4d05929ef41685312345
   Accept: application/json
   Content-type: application/json





Response
""""""""""""""""





This table shows the body parameters for the response:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|users                     |Userlist *(Required)*    |The users object returns |
|                          |                         |a collection of user     |
|                          |                         |objects that have the    |
|                          |                         |specified role.          |
+--------------------------+-------------------------+-------------------------+
|user                      |User *(Required)*        |The user object provides |
|                          |                         |this information for the |
|                          |                         |user with the specified  |
|                          |                         |role: ``id``,            |
|                          |                         |``enabled``,             |
|                          |                         |``username``, and        |
|                          |                         |``email``.               |
+--------------------------+-------------------------+-------------------------+







**Example Get users with role: XML response**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <users xmlns="http://docs.openstack.org/identity/api/v2.0" xmlns:atom="http://www.w3.org/2005/Atom">
       <user email="john.smith@example.org" enabled="true" id="123456" username="jqsmith"/>
       <user email="mike.turner@example.org" enabled="true" id="388493" username="miketurner"/>
       <user email="poe.joe@object.org" enabled="false" id="938439" username="poejo"/>
   </users>





**Example Get users with role: JSON response**


.. code::

   {
       "users": [
         {
           "id": "123456",
           "enabled": true,
           "username": "jqsmith",
           "email": "john.smith@example.org"
         },
         {
           "id": "388493",
           "enabled": true,
           "username": "miketurner",
           "email": "mike.turner@example.org"
         },
         {
           "id": "938439",
           "enabled": false,
           "username": "poejo",
           "email": "poe.joe@object.org"
         }
       ]
   }




