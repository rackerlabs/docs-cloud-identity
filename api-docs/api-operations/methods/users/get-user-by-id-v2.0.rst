.. _get-user-by-id-v2.0:

Get user by id
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /v2.0/users/{userId}

This operation returns the following detailed account information for a specific user, 
by user id: email address, user name, user id, status, default region, and domain id.

.. note::

   If this request is issued by a user holding the admin role (``identity:user-admin``), 
   the specific user's information is returned only if that user is associated with the 
   same tenant as the requester's ``user-admin`` token.
   
   If this request is issued by a user holding the user role (``identity:default``), 
   the response only includes the user account information for the user who submitted the 
   request. 

This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |The operation completed  |
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

This operation does not accept a request body.

Response
""""""""""""""""


**Example: Get user by id HTTP response header: XML**


.. code::

   HTTP/1.1 200 OK
   Content-Type: application/xml
   
   
**Example: Get user by id: XML response**

.. code:: 

   <?xml version="1.0" encoding="UTF-8"?>
   <user 
         xmlns="http://docs.openstack.org/identity/api/v2.0" 
         xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0" 
         xmlns:atom="http://www.w3.org/2005/Atom" 
         xmlns:rax-kskey="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0" 
         xmlns:os-ksec2="http://docs.openstack.org/identity/api/ext/OS-KSEC2/v1.0" 
         xmlns:rax-ksqa="http://docs.rackspace.com/identity/api/ext/RAX-KSQA/v1.0" 
         xmlns:ns7="http://docs.rackspace.com/identity/api/ext/RAX-KSGRP/v1.0" 
         xmlns:os-ksadm="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
         rax-auth:domainId="5830280" 
         rax-auth:defaultRegion="DFW" 
         rax-auth:multiFactorEnabled="true" 
         rax-auth:multiFactorState="ACTIVE" 
         rax-auth:userMultiFactorEnforcementLevel="OPTIONAL"
         id="123456" 
         username="jqsmith" 
         email="john.smith@example.org" 
         enabled="true"/>
   
   
**Example: Get user by id HTTP response header: json**


.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
      

**Example: Get user by id response: json**


.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   
   {
     "user": 
       {
         "rax-auth:domainId":"5830280"
         "id": "123456",
         "enabled": true,
         "username": "jqsmith",
         "email": "john.smith@example.org",
         "rax-auth:defaultRegion":"DFW",
         "rax-auth:multiFactorEnabled":"true",
         "rax-auth:multiFactorState":"ACTIVE",
         "rax-auth:userMultiFactorEnforcementLevel":"OPTIONAL"
       }
   }
   




