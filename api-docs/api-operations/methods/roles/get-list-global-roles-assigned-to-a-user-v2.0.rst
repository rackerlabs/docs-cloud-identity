.. _get-list-global-roles-assigned-to-a-user-v2.0:

List global roles assigned to a user
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /v2.0/users/{userId}/roles

This operation returns a list of :ref:`global roles <role-concept>` 
that are assigned to the account with the specified user Id. If you don't know the ID, 
use the :ref:`Get user by Id <get-user-by-id-v2.0>` operation to find it.

For each role listed, the response includes identifying information such as the role ID 
(such as ``123`` ), name (such as ``Admin``, and description (such as ``All Access``). 
The list of global roles excludes any tenant roles associated with this user.

.. note::

   - This call is available to users who hold either the admin role (``identity:user-admin``) 
     or the user role ( ``identity:default`` ).
     
   - For users holding the ``user`` role, the call is valid only if ``userId`` and the 
     ``user-default`` token have the same value for ``tenant``.
   
   
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

**Example List global roles assigned to a user: XML request**


.. code::

   GET /v2.0/users/123456/roles HTTP/1.1
   Host: identity.api.rackspacecloud.com
   X-Auth-Token: 771dd18634734a46b49f2af620112345
   Accept: application/xml
   Content-type: application/xml
   


**Example List global roles assigned to a user: JSON request**


.. code::

   GET /v2.0/users/123456/roles HTTP/1.1
   Host: identity.api.rackspacecloud.com
   X-Auth-Token: 771dd18634734a46b49f2af620112345
   Accept: application/json
   Content-type: application/json
   





Response
""""""""""""""""

**Example List global roles assigned to a user: XML response**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
     <roles 
       xmlns:atom="http://www.w3.org/2005/Atom" 
       xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0" 
       xmlns="http://docs.openstack.org/identity/api/v2.0" 
       xmlns:ns4="http://docs.rackspace.com/identity/api/ext/RAX-KSGRP/v1.0" 
       xmlns:rax-ksqa="http://docs.rackspace.com/identity/api/ext/RAX-KSQA/v1.0" 
       xmlns:os-ksadm="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0" 
       xmlns:rax-kskey="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0" 
       xmlns:os-ksec2="http://docs.openstack.org/identity/api/ext/OS-KSEC2/v1.0">
       
       <role id="100" name="devops" description="DevOps center" serviceId="cke5372rw2rty8bb70a0e702a4626977x4406e5" rax-auth:propagate="true"/>
       <role id="30007896" name="acctCreator:public" description="Account creator public role" serviceId="cke5372ebabeeabb70a0e702a4626977x4406e5" rax-auth:propagate="false"/>
       <role id="30007897" name="acctCreator:trusted" description="Account creator trusted role" serviceId="bde1268ebabeeabb70a0e702a4626977c331d5c4" rax-auth:propagate="false"/>
       <role id="30007653" name="database:admin" description="admin role for cloud files" serviceId="bde1268ebabeeabb70a0e702a4626977c331d5c4" rax-auth:propagate="false"/> 
   </roles>
   
   

**Example List global roles assigned to a user: JSON response**


.. code::

   {
       "roles": [
           {
               "description": "DevOps center",
               "id": "100",
               "name": "devops",
               "serviceId": "cke5372rw2rty8bb70a0e702a4626977x4406e5"
           },
           {
               "description": "Account creator public role",
               "id": "30007896",
               "name": "acctCreator:public",
               "serviceId": "cke5372ebabeeabb70a0e702a4626977x4406e5"
           },
           {
               "description": "Admin creator trusted role",
               "id": "30007897",
               "name": "acctCreator:trusted",
               "serviceId": "cke5372ebabeeabb70a0e702a4626977x4406e5"
           },
           {
               "description": "Admin role for database service",
               "id": "30007653",
               "name": "database:admin",
               "serviceId": "cke5372ebabeeabb70a0e702a4626977x4406e5"
           },
          
       ]
   }




