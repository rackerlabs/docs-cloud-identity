
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-list-users-v2.0-users:

List users
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v2.0/users

Lists users.

This request returns a users object that lists information for each user. Information includes the email, name, user ID, status, and account settings for the specified account. Use the ``name`` and ``email`` query parameters to find information about a specific user account. 

* If this request is issued by a user holding the admin role ( ``identity:user-admin`` ), it returns a list of all users for the tenant. To find a single user, include the ``name`` in the request.
* If this request is issued by a user holding the user role ( ``identity:default`` ), the operation only returns information about the user's account.
* To find the user with the authority to modify account permissions, refer to `"Get User Admin." <GET_getUserAdmin_v2.0_admins_User_Calls.html>`__






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



This table shows the query parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|name                      |String *(Optional)*      |Specify the user name to |
|                          |                         |look up.                 |
+--------------------------+-------------------------+-------------------------+
|email                     |String *(Optional)*      |User email address.      |
+--------------------------+-------------------------+-------------------------+




This operation does not accept a request body.




Response
""""""""""""""""










**Example List users: XML response**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <users 
         xmlns="http://docs.openstack.org/identity/api/v2.0"
         xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0" 
         xmlns:atom="http://www.w3.org/2005/Atom">
         <user 
               email="john.smith@example.org" 
               enabled="true" id="123456" 
               username="jqsmith"/>
         
         <user email="mike.turner@example.org" 
               enabled="true" id="388493" 
               username="miketurner"/>
         
         <user email="poe.joe@object.org" 
               enabled="false" 
               id="938439" 
               username="poejo"/>
   </users>
   





**Example List users: JSON response**


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




