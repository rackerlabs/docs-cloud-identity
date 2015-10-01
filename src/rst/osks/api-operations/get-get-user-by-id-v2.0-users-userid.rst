
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-get-user-by-id-v2.0-users-userid:

Get user by Id
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v2.0/users/{userId}

Gets detailed account information for a user with the specified ID.

This operation returns the following information for each account associated with the specified user ID: email address, user name, user ID, status, default region, and domain id.



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
|{userId}                  |String *(Required)*      |The ID of the user for   |
|                          |                         |which you want to        |
|                          |                         |perform the request.     |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




Response
""""""""""""""""










**Example Get user by Id: XML response**


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





**Example Get user by Id: JSON response**


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




