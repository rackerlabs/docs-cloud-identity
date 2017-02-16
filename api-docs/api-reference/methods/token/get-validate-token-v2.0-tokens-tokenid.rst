.. _get-validate-token-v2.0:

Validate token
~~~~~~~~~~~~~~

.. code::

    GET /v2.0/tokens/{tokenId}

Use the Validate token operation to verify that the specified token is valid
and owned by the specified tenant.

In the ``/tokens/{tokenId}`` path, valid tokens exist and invalid tokens do
not.  For application development, use the Validate token operation to make
sure that  the client submitting the Validate token request can handle an
ItemNotFound (``404``) error for an invalid token.

If the operation is successful, rerun the tenant credentials to return the
permissions relevant to a particular client.

Any user can validate their own token. Users with the ``identity:admin`` or
``idenity:user-admin`` role can validate the token for any account user.


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
-------

This table shows the header and URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|X-Auth-Token              |Header                   |A valid admin            |
|                          |String *(Required)*      |authentication token.    |
+--------------------------+-------------------------+-------------------------+


This table shows the query parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|belongsTo                 |String *(Optional)*      |Validate that a token    |
|                          |                         |has the specified tenant |
|                          |                         |in scope.                |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.


Response
--------

**Example: Validate token: XML response**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <access
     xmlns:os-ksadm="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
     xmlns="http://docs.openstack.org/identity/api/v2.0">
     <token id="xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx "
       expires="2010-11-01T03:32:15-05:00">
       <tenant id="345" name="My Project" />
     </token>
     <user
       xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
       id="123" username="testuser" rax-auth:defaultRegion="DFW">
       <roles xmlns="http://docs.openstack.org/identity/api/v2.0">
         <role id="123" name="compute:admin" />
         <role id="234" name="object-store:admin" />
       </roles>
     </user>
   </access>

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <access
     xmlns="http://docs.openstack.org/identity/api/v2.0"
     xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
     xmlns:rax-kskey="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"
     xmlns:os-ksec2="http://docs.openstack.org/identity/api/ext/OS-KSEC2/v1.0"
     xmlns:rax-ksqa="http://docs.rackspace.com/identity/api/ext/RAX-KSQA/v1.0"
     xmlns:atom="http://www.w3.org/2005/Atom"
     xmlns:ns7="http://docs.rackspace.com/identity/api/ext/RAX-KSGRP/v1.0"
     xmlns:os-ksadm="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0">
     <token expires="2015-06-28T01:34:29.300Z" id="cd45ad90d8034a1b8d75aa0efa89060b">
       <tenant name="5830280" id="5830280"/>
       <rax-auth:authenticatedBy>
         <rax-auth:credential>APIKEY</rax-auth:credential>
       </rax-auth:authenticatedBy>
     </token>
     <user rax-auth:defaultRegion="SYD" name="maeker12" id="92bb036af5b0467198cded345597f6b4">
       <roles>
         <role rax-auth:propagate="false" serviceId="bde1268ebabeeabb70a0e702a4626977c331d5c4" description="Cloud Networks" name="CloudNetworks-Security-Groups" id="88"/>
         <role rax-auth:propagate="true" tenantId="5830280" serviceId="a45b14e394a57e3fd4e45d59ff3693ead204998b" description="A Role that allows a user access to keystone Service methods" name="compute:default" id="684"/>
         <role rax-auth:propagate="false" serviceId="bde1268ebabeeabb70a0e702a4626977c331d5c4" description="Default Role." name="identity:default" id="2"/>
         <role rax-auth:propagate="false" serviceId="bde1268ebabeeabb70a0e702a4626977c331d5c4" description="Admin role for access to all capabilities for all products" name="admin" id="10015034"/>
       </roles>
     </user>
   </access>





**Example: Validate token: JSON response**


.. code::

   {
       "access": {
           "token": {
               "id": "cd45ad90d8034a1b8d75aa0efa123456",
               "expires": "2015-06-28T01:34:29.300Z",
               "tenant": {
                   "id": "5830345",
                   "name": "5830345"
               },
               "RAX-AUTH:authenticatedBy": [
                   "APIKEY"
               ]
           },
           "user": {
               "id": "92bb036af5b0467198cded3455123456",
               "roles": [
                   {
                       "id": "88",
                       "serviceId": "bde1268ebabeeabb70a0e702a4626977c331d5c4",
                       "description": "Cloud Networks",
                       "name": "CloudNetworks-Security-Groups"
                   },
                   {
                       "tenantId": "5830345",
                       "id": "684",
                       "serviceId": "a45b14e394a57e3fd4e45d59ff3693ead204998b",
                       "description": "A Role that allows a user access to keystone Service methods",
                       "name": "compute:default"
                   },
                   {
                       "id": "2",
                       "serviceId": "bde1268ebabeeabb70a0e702a4626977c331d5c4",
                       "description": "Default Role.",
                       "name": "identity:default"
                   },
                   {
                       "id": "10015034",
                       "serviceId": "bde1268ebabeeabb70a0e702a4626977c331d5c4",
                       "description": "Admin role for access to all capabilities for all products",
                       "name": "admin"
                   }
               ],
               "name": "accountUserName",
               "RAX-AUTH:defaultRegion": "SYD"
           }
       }
   }





**Example: Validate token for impersonation response: JSON**


.. code::

   {
     "access":{
         "token":{
             "id":"xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
             "expires":"2010-11-01T03:32:15-05:00",
             "tenant":{
                 "id": "yourTenantID",
                 "name": "My Project"
              }
          },

         "user":{
             "id":"123",
             "name":"yourUsername",
             "roles":[{
                        "id":"123",
                        "name":"compute:admin"
                      },
                      {
                        "id":"234",
                        "name":"object-store:admin",
                      }
              ]
          },

          "RAX-AUTH:impersonator":{
               "id":"567",
               "name":"impersonator.username",
               "roles":[{
                          "id":"123",
                          "name":"Racker"
                        },
                        {
                           "id":"234",
                           "name":"object-store:admin",
                        }
              ]
          }
     }
   }






**Example: Validate Token for Impersonation Response: XML**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <access xmlns="http://docs.openstack.org/identity/api/v2.0"
       xmlns:RAX-AUTH="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0">
       <token id="xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
           expires="2010-11-01T03:32:15-05:00">
           <tenant id="yourTenantID"
               name="My Project" />
       </token>
       <user id="123"
           username="yourUserName">
           <roles xmlns="http://docs.openstack.org/identity/api/v2.0">
               <role id="123" name="compute:admin" />
               <role id="234" name="object-store:admin" />
           </roles>
       </user>
       <RAX-AUTH:impersonator id="567"
           username="impersonator.UserName">
           <roles xmlns="http://docs.openstack.org/identity/api/v2.0">
               <role id="123" name="Racker" />
               <role id="234" name="object-store:admin" />
           </roles>
       </RAX-AUTH:impersonator>
   </access>





**Example: Validate token for Racker response: JSON**


.. code::

   {
     "access": {
       "token": {
         "expires": "2013-10-26T14:34:02.255Z",
         "id": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
       },
       "user": {
         "RAX-AUTH:defaultRegion": "",
         "roles": [
           {
             "name": "Racker",
             "description": "Defines a user as being a Racker",
             "id": "9",
             "serviceId": "18e7a7032733486cd32f472d7bd58f709ac0d221"
           }
         ],
         "id": "userId"
       }
     }
   }



**Example: Validate token for Racker response: XML**


.. code::

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <access xmlns="http://docs.openstack.org/identity/api/v2.0"
       xmlns:ns2="http://www.w3.org/2005/Atom"
       xmlns:os-ksadm="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
       xmlns:rax-ksqa="http://docs.rackspace.com/identity/api/ext/RAX-KSQA/v1.0"
       xmlns:rax-kskey="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"
       xmlns:os-ksec2="http://docs.openstack.org/identity/api/ext/OS-KSEC2/v1.0"
       xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0">
       <token id="xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
           expires="2013-11-26T18:08:51.146Z"/>
       <user id="racerSSOUsername">
           <roles>
               <role id="9" name="Racker"
                   description="Defines a user as being a Racker"
                   serviceId="18e7a7032733486cd32f472d7bd58f709ac0d221"/>
               <role name="dl_RackUSA"/>
               <role name="dl_RackGlobal"/>
               <role name="dl_cloudblock"/>
               <role name="dl_US Managers"/>
               <role name="DL_USManagers"/>
           </roles>
       </user>
   </access>
