.. _get-user-admin-v2.0:

Get user admin
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v2.0/users/{userId}/RAX-AUTH/admins

Account users with the ``identity:user-admin`` or ``identity:default`` role can use 
this operation to identify the administrator or point of contact for a user account 
if they have questions or need assistance regarding user or role management. 

This request returns the following identifying information about the administrator: 
domain name, domain ID, email address, status, user ID and user name.


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
|503                       |Service Fault            |Service is not available.|
+--------------------------+-------------------------+-------------------------+


Request
""""""""""""""""

This table shows the header and URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|X-Auth-Token              |Header                   |A valid admin            |
|                          |String *(Required)*      |authentication token.    |
+--------------------------+-------------------------+-------------------------+
|{userId}                  |URI                      |The unique, system-      |
|                          |String *(Required)*      |generated user ID for an |
|                          |                         |account.                 |
+--------------------------+-------------------------+-------------------------+


This operation does not accept a request body.

Response
""""""""""""""""

****Example:  Get user admin: XML response**


.. code::

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <users xmlns="http://docs.openstack.org/identity/api/v2.0" 
       xmlns:ns2="http://www.w3.org/2005/Atom"
       xmlns:os-ksadm="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0" 
       xmlns:rax-ksqa="http://docs.rackspace.com/identity/api/ext/RAX-KSQA/v1.0" 
       xmlns:rax-kskey="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0" 
       xmlns:os-ksec2="http://docs.openstack.org/identity/api/ext/OS-KSEC2/v1.0" 
       xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0">
       <user id="10022879" 
           username="JuserAdmin" 
           enabled="true" 
           display-name="JuserAdmin" 
           rax-auth:defaultRegion="USA" 
           rax-auth:domainId="5701091"/>
   </users>


****Example:  Get user admin: JSON response**


.. code::

   {
       "users": [
           {
               "RAX-AUTH:defaultRegion": "",
               "RAX-AUTH:domainId": "12345",
               "email": "userAdmin@rack.com",
               "enabled":"true",
               "id": "10022879",
               "username": "JuserAdmin"
           }
       ]
   }




