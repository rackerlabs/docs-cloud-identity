
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-get-user-by-id-users-id:

Get user by Id
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /users/{id}

Get detailed account information for a specific user, by userid.

This request returns the following information for each account associated with the specified user ID: email address, username, user ID, status, default region, and domain id.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |Get user by id: XML      |                         |
|                          |response                 |                         |
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
|X-Auth-Token              |String *(Required)*      |A valid authentication   |
|                          |                         |token with               |
|                          |                         |administrative access.   |
+--------------------------+-------------------------+-------------------------+
|{id}                      |String *(Required)*      |The id associated with   |
|                          |                         |the user account you     |
|                          |                         |want to look up.         |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




Response
""""""""""""""""










**Example Get user by id: XML response**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <user xmlns="http://docs.openstack.org/identity/api/v2.0"
         xmlns:ns2="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
         xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
         id="123456" username="jqsmith"
         enabled="true"
         email="john.smith@example.org"
         RAX-AUTH:defaultRegion="DFW"
         RAX-AUTH:domainId="5830280"
         RAX-AUTH:multiFactorEnabled="true" >
   </user>





**Example Get user by id: json response**


.. code::

   {
     "user": {
     
       "id": "123456",
       "username": "jqsmith",
       "email": "john.smith@example.org",
       "enabled": true,
       "RAX-AUTH:defaultRegion":"DFW",
       "RAX-AUTH:domainId":"5830280",
       "RAX-AUTH:multiFactorEnabled": true
       
     }
   }




