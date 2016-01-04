.. _post-update-user-information-and-password-v2.0:

Update user information and password
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /v2.0/users/{userId}

This operation updates the user information for the account associated with the specified 
user id. Before you submit the update request, use the :ref:`Get user by id <get-user-by-id-v2.0>` 
operation to verify that the user name, email account, and status associated with ``userId`` 
match the account you want to update.

Only include those user data elements that you wish to modify in the request body. 
For example, if you only need to update the user's email, for don't include the other 
body parameters like ``id``, ``enabled``, or ``rax-auth:domainId``.

.. note::
      
    -  Users who hold the admin role can update users who hold the user role 
       (``identity:default``) or the admin role (``identity:user-admin``) for the same tenant.
      
    -  Administrators can change the default region for another user, but the new value 
       must be one of the regions listed for a Cloud Compute endpoint in the service catalog.
      
    -  Administrators can change a user default region, but the new value must be one of 
       the regions listed for a Cloud Compute endpoint in the service catalog.
   

This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |Success. The tenant is   |
|                          |                         |authenticated.           |
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
""""""""""""""""

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


This table shows the body parameters for the request:

+--------------------------+-------------------------+-----------------------------+
|Name                      |Type                     |Description                  |
+==========================+=========================+=============================+
|name                      |String *(Required)*      |The user name. The value     |
|                          |                         |must begin with an alpha     |
|                          |                         |character.                   |
+--------------------------+-------------------------+-----------------------------+
|email                     |String *(Optional)*      |The user email.              |
+--------------------------+-------------------------+-----------------------------+
|enabled                   |Boolean *(Optional)*     |Indicates whether the        |
|                          |                         |user is enabled (true)       |
|                          |                         |or disabled (false).         |
|                          |                         |Users cannot update          |
|                          |                         |the``enabled`` status on     |
|                          |                         |their own account.           |
+--------------------------+-------------------------+-----------------------------+
|RAX-AUTH:defaultRegion    |String *(Optional)*      |The default region that      |
|                          |                         |the user is assigned to.     |
|                          |                         |Must be one of the           |
|                          |                         |regions available in the     |
|                          |                         |service catalog.             |
+--------------------------+-------------------------+-----------------------------+
|OS-KSADM:password         |String *(Optional)*      |Specify an initial           |
|                          |                         |password for the user        |
|                          |                         |account. If this value       |
|                          |                         |is not specified, the        |
|                          |                         |Identity service             |
|                          |                         |automatically generates      |
|                          |                         |a password. Ensure that      |
|                          |                         |the value you specify        |
|                          |                         |meets the following          |
|                          |                         |criteria:                    |
|                          |                         |                             |
|                          |                         |* Length must be at least    |                
|                          |                         |  8 characters; no maximum.  |                       
|                          |                         |                             |
|                          |                         |* Can include uppercase,     |
|                          |                         |  lower case, and numeric    |
|                          |                         |  characters.                |
|                          |                         |                             |
|                          |                         |* Can start                  |
|                          |                         |  with or include any of     |
|                          |                         |  the following special      |
|                          |                         |  characters: ~ ! @ # % ~    |
|                          |                         |  & * _ - | \ ( ) { } [ ]    |
|                          |                         |  : ; " ' < >,. ? /          |
|                          |                         |                             |
|                          |                         |* Password cannot begin      |
|                          |                         |  with a space, but it can   |
|                          |                         |  contain a space.           |
|                          |                         |                             |
+--------------------------+-------------------------+-----------------------------+


**Example:  Update user HTTP request header: XML**


.. code::

   POST /v2.0/users/123456 HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/xml
   Content-type: application/xml
   X-Auth-Token: eaf8345057414cd397d0543123456789
   
   
**Example:  Update user HTTP request header: JSON**


.. code::

   POST /v2.0/users/123456 HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/json
   Content-type: application/json
   X-Auth-Token: eaf8345057414cd397d0543123456789


**Example:  Update user request: XML**

.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <user xmlns="http://docs.openstack.org/identity/api/v2.0"
         xmlns:ns2="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
         xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
         username="jqsmith"
         enabled="true"
         email="john.smith@example.org">
   </user>


**Example:  Update user request: JSON**


.. code::

   {
     "user": {
       "username": "jqsmith",
       "email": "john.smith@example.org",
       "enabled": true
     }
   }

**Example:  Update user password HTTP request header: XML**


.. code::

   POST /v2.0/users/123456 HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/xml
   Content-type: application/xml
   X-Auth-Token: eaf8345057414cd397d0543123456789
   
   
**Example:  Update user password HTTP request header: JSON**


.. code::

   POST /v2.0/users/123456 HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/xml
   Content-type: application/json
   X-Auth-Token: eaf8345057414cd397d0543123456789 
     

**Example:  Update user password request: XML**


.. code::

   <user username="abc123"  
       ns1:password="ungu355ab13" 
       xmlns:ns1="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0" 
       xmlns:ns2="http://docs.openstack.org/identity/api/v2.0" />
       

**Example:  Update user password request: JSON**


.. code::

   {
       "user": {
               "username": "abc123",  
               "OS-KSADM:password":"ungu355ab13"
           }
   }


Response
""""""""""""""""

**Example:  Update user information and password: XML response**


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


**Example:  Update user information and password: JSON response**


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




