
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-list-users-v2.0-users:

List users
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v2.0/users

Lists users.

This operation returns a list of users with detailed account information about each user including email, name, user ID, account configuration and status information... note::
Notes



* If this request is issued by a user holding the Identity admin role ( ``identity:user-admin`` ), it returns a list of all users for the tenant. To find a single user, include the ``name`` in the request.
* If this request is issued by a user holding the Identity user role ( ``identity:default`` ), the operation only returns information about the user account.
* To find the user with the authority to modify account permissions, refer to `"Get User Admin." <GET_getUserAdmin_v2.0_admins_User_Calls.html>`__








This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |The request has          |
|                          |                         |succeeded.               |
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
|X-Auth-Token              |String *(Required)*      |A valid admin            |
|                          |                         |authentication token.    |
+--------------------------+-------------------------+-------------------------+



This table shows the query parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|name                      |String *(Optional)*      |Specify the user name to |
|                          |                         |look up.                 |
+--------------------------+-------------------------+-------------------------+
|email                     |String *(Optional)*      |Specify the email        |
|                          |                         |address to look up.      |
+--------------------------+-------------------------+-------------------------+




This operation does not accept a request body.




**Example List users: HTTP request**


.. code::

   GET /v2.0/users/12342b4ddb594819b697d0048614c117 HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/json
   X-Auth-Token: 0cb090705e82443fa71471e9c3456789
   Content-type: application/xml
   





**Example List users: HTTP request**


.. code::

   GET /v2.0/users/12342b4ddb594819b697d0048614c117 HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/json
   X-Auth-Token: 0cb090705e82443fa71471e9c3456789
   Content-type: application/json
   





Response
""""""""""""""""





This table shows the body parameters for the response:

+-------------------------------------+-------------+---------------------------------------+
|Name                                 |Type         |Description                            |
+=====================================+=============+=======================================+
|users                                |Object       |Returns the collection of users who    |
|                                     |*(Required)* |match the specification in the List    |
|                                     |             |user API request.                      |
+-------------------------------------+-------------+---------------------------------------+
|user                                 |Object       |A user object that provides user       |
|                                     |*(Required)* |account information:                   |
+-------------------------------------+-------------+---------------------------------------+
|RAX-AUTH:defaultRegion               |String       |The default region that the user is    |
|                                     |*(Optional)* |assigned to. Must be one of the        |
|                                     |             |regions available in the service       |
|                                     |             |catalog.                               |
+-------------------------------------+-------------+---------------------------------------+
|RAX-AUTH:domainId                    |String       |The ID for the domain that the user    |
|                                     |*(Optional)* |account has been assigned to.          |
+-------------------------------------+-------------+---------------------------------------+
|RAX-AUTH:multiFactorEnabled          |Boolean      |If an account has been configured to   |
|                                     |*(Optional)* |use multi-factor authentication, this  |
|                                     |             |field indicates whether multi-factor   |
|                                     |             |authentication is currently enabled or |
|                                     |             |disabled.                              |
+-------------------------------------+-------------+---------------------------------------+
|RAX-AUTH:multiFactorState            |String       |This extended attribute indicates      |
|                                     |*(Optional)* |whether a multifactor-enabled user     |
|                                     |             |account is locked as a result of       |
|                                     |             |failed authentication attempts. If the |
|                                     |             |account has been locked at any point,  |
|                                     |             |the value is either ``LOCKED`` or      |
|                                     |             |``ACTIVE``. User administrators can    |
|                                     |             |use the Update multi-factor            |
|                                     |             |authentication settings on account     |
|                                     |             |operation to restore access to a       |
|                                     |             |locked account.                        |
+-------------------------------------+-------------+---------------------------------------+
|RAX-                                 |String       |If present, this extended attribute    |
|AUTH:userMultiFactorEnforcementLevel |*(Optional)* |specifies the multi-factor             |
|                                     |             |authentication enforcement policy that |
|                                     |             |applies to the specified account. *    |
|                                     |             |``REQUIRED`` The user must use multi-  |
|                                     |             |factor authentication to log in to     |
|                                     |             |their Rackspace Cloud account. `domain |
|                                     |             |enforcement                            |
|                                     |             |<PUT_updateMultiFactorDomain_v2.0_RAX- |
|                                     |             |AUTH_domains__domainId__multi-         |
|                                     |             |factor_.html>`__ domain level          |
|                                     |             |enforcement is configured as           |
|                                     |             |``Optional``. * ``OPTIONAL.`` The user |
|                                     |             |has the option to authenticate using   |
|                                     |             |multi-factor authentication. *         |
|                                     |             |``DEFAULT.`` The user multi-factor     |
|                                     |             |authentication requirements are        |
|                                     |             |determined by the domain level         |
|                                     |             |enforcement setting for multi-factor   |
|                                     |             |authentication.                        |
+-------------------------------------+-------------+---------------------------------------+







**Example List users: HTTP response**


.. code::

   HTTP/1.1 200 OK
   Content-Type: application/xml
   





**Example List users: XML response**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <users 
         xmlns:atom="http://www.w3.org/2005/Atom" 
         xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0" 
         xmlns="http://docs.openstack.org/identity/api/v2.0" 
         xmlns:ns4="http://docs.rackspace.com/identity/api/ext/RAX-KSGRP/v1.0" 
         xmlns:rax-ksqa="http://docs.rackspace.com/identity/api/ext/RAX-KSQA/v1.0" 
         xmlns:os-ksadm="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0" 
         xmlns:rax-kskey="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0" 
         xmlns:os-ksec2="http://docs.openstack.org/identity/api/ext/OS-KSEC2/v1.0" >
        
         <user 
               rax-auth:domainId="5830280" 
               rax-auth:defaultRegion="DFW" 
               rax-auth:multiFactorEnabled="true" 
               rax-auth:multiFactorState="ACTIVE" 
               rax-auth:userMultiFactorEnforcementLevel="OPTIONAL"
               rax-auth:multi
               id="123456" 
               username="jqsmith" 
               email="john.smith@example.org" 
               enabled="true"/>
         
         <user 
               rax-auth:domainId="5830280" 
               rax-auth:defaultRegion="DFW" 
               rax-auth:multiFactorEnabled="false" 
               id="938439" 
               username="poejo" 
               email="poe.joe@object.org" 
               enabled="true"/>
   </users>





**Example List users: HTTP response**


.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   





**Example List users: JSON response**


.. code::

   {
     "users": [
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
       },
       {
         "rax-auth:domainId":"5830280"
           "id": "938439",
           "enabled": false,
           "username": "poejo",
           "email": "poe.joe@example.org",
           "rax-auth:defaultRegion":"DFW",
           "rax-auth:multiFactorEnabled":"false"
         },
       }  
     ]
   }
   




