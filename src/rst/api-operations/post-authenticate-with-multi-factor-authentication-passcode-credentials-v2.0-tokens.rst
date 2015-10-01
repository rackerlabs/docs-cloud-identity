
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _post-authenticate-with-multi-factor-authentication-passcode-credentials-v2.0-tokens:

Authenticate with multi-factor authentication passcode credentials
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /v2.0/tokens

Authenticate with multi-factor passcode credentials.

.. important::
   User accounts that use multi-factor authentication must authenticate with Identity service version 2.0 or later. Attempts to authenticate with earlier API versions will fail.
   
   

If an account is enabled for multi-factor authentication, authentication is a two-step process: 

#. Send an initial with `user name and password credentials <POST_authenticate_v2.0_tokens_Token_Calls.html>`__.

The request triggers Identity service to send an SMS message to the phone associated with the user account. In response to the authentication request, Identity service returns a 401 message that includes a session ID in the WWW-Authenticate header and a request for additional credentials.
#. Send an additional authentication request providing the ``sessionId`` and multi-factor authentication passcode included in the SMS message from Identity service verification service.






This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |The request succeeded.   |
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |Unauthorized error can   |
|                          |                         |occur if the passcode is |
|                          |                         |not valid, or if the     |
|                          |                         |user account is locked   |
|                          |                         |because the user has     |
|                          |                         |exceeded the maximum     |
|                          |                         |number of attempts to    |
|                          |                         |authenticate. Use the    |
|                          |                         |Unlock user account      |
|                          |                         |operation to remove the  |
|                          |                         |account lock.            |
+--------------------------+-------------------------+-------------------------+
|403                       |User Disabled            |User account has been    |
|                          |                         |disabled.                |
+--------------------------+-------------------------+-------------------------+
|415                       |Bad Media Type           |Bad media type. This may |
|                          |                         |result if the wrong      |
|                          |                         |media type is used in    |
|                          |                         |the API request. Check   |
|                          |                         |the content-type and     |
|                          |                         |accept headers included  |
|                          |                         |in the request.          |
+--------------------------+-------------------------+-------------------------+
|500                       |Service Fault            |Passcode not accepted.   |
+--------------------------+-------------------------+-------------------------+


Request
""""""""""""""""








This operation does not accept a request body.




**Example Authenticate with multi-factor credentials: XML request with header**


.. code::

   POST /v2.0/tokens HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Content-Type: application/xml
   Accept: application/xml
   X-SessionId: APU9ymNjSKJG21HVdiRdOg0rk2fqh7uQ1FafVDXo3SId6nMHjUkKSDacFwDLGCC9U_DKI6Lwzu-wMi3LIWT-bA24EdGYdycM3rKzAfVPiCCjigN315ZLJo5s2TmiGQTSW9b5H7euQjJ6KBTk5elT2l8HrPH-9rrBjw 
   
   <auth xmlns="http://docs.openstack.org/identity/api/v2.0"
   	xmlns:RAX-AUTH="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0" 
   	xmlns:atom="http://www.w3.org/2005/Atom">
   	<RAX-AUTH:passcodeCredentials factor="PASSCODE" passcode="123456"/>
   </auth>
   





**Example Authenticate with multi-factor authentication credentials: JSON request with header**


.. code::

   POST /v2.0/tokens HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Content-Type: application/json
   Accept: application/json
   X-SessionId: APU9ymNjSKJG21HVdiRdOg0rk2fqh7uQ1FafVDXo3SId6nMHjUkKSDacFwDLGCC9U_DKI6Lwzu-wMi3LIWT-bA24EdGYdycM3rKzAfVPiCCjigN315ZLJo5s2TmiGQTSW9b5H7euQjJ6KBTk5elT2l8HrPH-9rrBjw
   
   {
   "auth": {
   "RAX-AUTH:passcodeCredentials": {
   "passcode":”123456"
   }
   }
   }





Response
""""""""""""""""










**Example Authenticate with multi-factor authentication credentials: XML response with header**


.. code::

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <access 
   	xmlns:atom="http://www.w3.org/2005/Atom" 
   	xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0" 
   	xmlns="http://docs.openstack.org/identity/api/v2.0" 
   	xmlns:ns4="http://docs.rackspace.com/identity/api/ext/RAX-KSGRP/v1.0" 
   	xmlns:rax-ksqa="http://docs.rackspace.com/identity/api/ext/RAX-KSQA/v1.0" 
   	xmlns:os-ksadm="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0" 
   	xmlns:rax-kskey="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0" 
   	xmlns:os-ksec2="http://docs.openstack.org/identity/api/ext/OS-KSEC2/v1.0">
   
     <token 
     	id="449f04aca3594ce38e5b0b18fce6bfad" 
     	expires="2014-01-09T15:08:53.645-06:00">
     
       <rax-auth:authenticatedBy>
         	<rax-auth:credential>PASSWORD</rax-auth:credential>
      	</rax-auth:authenticatedBy>  		
     	</token>
     
     <user 
     	id= "ec7f0fd2de2f4eeeb07c7412c848fe69" 
     	name="jqsmith" 
     	rax-auth:defaultRegion="DFW" 
     	rax-auth:federated="false">
     		
     	<roles>
         <role 
         	id="3" 
         	name="identity:user-admin"
         	description="User Admin Role."/>
   		</roles>		
     	</user>
     
     <serviceCatalog/>  
   </access>
   





**Example Authenticate with multi-factor credentials: JSON response with header**


.. code::

   < HTTP/1.1 200 OK
   < Vary:  Accept, Accept-Encoding, X-Auth-Token
   < Content-Type: application/json
   < Content-Length: 387
   < Server: Jetty(6.1.25)
   {
       "access": {
           "serviceCatalog": [],
           "token": {
               "RAX-AUTH:authenticatedBy": [
                   "PASSCODE",
                   "PASSWORD"
               ],
               "expires": "2014-01-09T15:08:53.645-06:00",
               "id": "abcdef123ghi4j5k67m8910n12op3qrs"
           },
           "user": {
               "RAX-AUTH:defaultRegion": "IAD",
               "RAX-AUTH:federated": false,
               "id": "789345",
               "name": "mfaTestUser",
               "roles": [
                   {
                       "description": "User Admin Role.",
                       "id": "3",
                       "name": "identity:user-admin"
                   }
               ]
           }
       }
   }




