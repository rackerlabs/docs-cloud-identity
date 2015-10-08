.. _post-authenticate-with-multi-factor-authentication-passcode-credentials-v2.0:

Authenticate with multi-factor authentication passcode credentials
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /v2.0/tokens

Use this API operation to submit Authenticate with multi-factor passcode credentials.

.. note::
   
   User accounts that use multi-factor authentication must authenticate with 
   Identity service version 2.0 or later. Attempts to authenticate with earlier API 
   versions will fail.

If an account is enabled to use multi-factor authentication, authentication is a two-step process: 

#. Send an initial POST token authentication request with either password or API credentials. 

    In response to the authentication request, the Identity service returns a 401 
    message that includes the ``X-SessionId`` parameter in the WWW-Authenticate header 
    and a request for additional credentials. The Identity service also sends the 
    multi-factor authentication passcode to the phone associated with the user account.
    
#. Send an additional authentication request that includes the ``X-SessionID`` 
   and the multi-factor authentication ``passcode``

See :ref:`Authenticate from a multifactor-enabled user account <auth-mfa-enabled-account>`  
for sample authentication requests in cURL format.

This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |Success. The tenant is   |
|                          |                         |authenticated.           |
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |You are not authorized   |
|                          |                         |to complete this         |
|                          |                         |operation.               |
+--------------------------+-------------------------+-------------------------+
|403                       |User Disabled            |User account has been    |
|                          |                         |disabled.                |
+--------------------------+-------------------------+-------------------------+
|500                       |Service Fault            |Service is not available.|
+--------------------------+-------------------------+-------------------------+


Request
""""""""""""""""

This table shows the header and URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|X-SessionId               |Header                   |The SessionId header     |
|                          |String *(Optional)*      |returned when a          |
|                          |                         |multifactor-enabled user |
|                          |                         |authenticates to         |
|                          |                         |Identity service with    |
|                          |                         |either Password or API   |
|                          |                         |key credentials.         |
|                          |                         |Required to authenticate |
|                          |                         |with multi-factor        |
|                          |                         |authentication Passcode  |
|                          |                         |credentials.             |
+--------------------------+-------------------------+-------------------------+
|{passcode}                |URI                      |Passcode received on the |
|                          |String *(Optional)*      |multifactor-enabled      |
|                          |                         |phone associated with    |
|                          |                         |the user account.        |
+--------------------------+-------------------------+-------------------------+


Request
""""""""""""""""

This table shows the body parameters for the request:

+-----------------------+--------------+---------------------------------------+
|Name                   |Type          |Description                            |
+=======================+==============+=======================================+
|RAX-AUTH:\             |Object        |Specifies the multi-factor             |
|passcodeCredentials    |              |passcode credentials for the           |
|                       |              |authentication request.                |
|                       |              |for multi-factor authentication.       |
|                       |              |Specify either of these values. *      |
|                       |              |``domainMultiFactorEnforcementLevel:   |
|                       |              |"REQUIRED"`` makes multi-factor        |
|                       |              |authentication mandatory for all       |
|                       |              |account users. *                       |
|                       |              |``domainMultiFactorEnforcementLevel:   |
|                       |              |"OPTIONAL"`` Users within the domain   |
|                       |              |can choose whether to use multi-factor |
|                       |              |authentication on their own accounts.  |
+-----------------------+--------------+---------------------------------------+
|RAX-AUTH:\             |String        |The domain enforcement level for       |
|passcodeCredentials    |              |multi-factor authentication. Specify   |
|**domainMultiFactor\   |              |one of the following values:           |
|EnforcementLevel**     |              |                                       |
|                       |              |- ``REQUIRED``                         |
|                       |              |   Authentication is mandatory for all |
|                       |              |   account users within the specified  | 
|                       |              |   domain.                             |    
|                       |              |                                       |    
|                       |              |- ``OPTIONAL``                         |
|                       |              |   Users within the specified domain   |
|                       |              |   can choose whether to use           | 
|                       |              |   multi-factor authentication         |           
|                       |              |   on their account.                   |    
|                       |              |                                       |    
+-----------------------+--------------+---------------------------------------+


**Example: Authenticate with multi-factor authentication credentials HTTP request header: XML**


.. code::

   POST /v2.0/tokens HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Content-Type: application/xml
   Accept: application/xml
   X-SessionId: APU9ymNjSKJG21HVdiRdOg0rk2fqh7uQ1FafVDXo3SId6nMHjUkKSDacFwDLGCC9U_DKI6Lwzu-wMi3LIWT-bA24EdGYdycM3rKzAfVPiCCjigN315ZLJo5s2TmiGQTSW9b5H7euQjJ6KBTk5elT2l8HrPH-9rrBjw 



**Example: Authenticate with multi-factor authentication credentials request: XML**

.. code::
   
   <auth xmlns="http://docs.openstack.org/identity/api/v2.0"
   	xmlns:RAX-AUTH="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0" 
   	xmlns:atom="http://www.w3.org/2005/Atom">
   	<RAX-AUTH:passcodeCredentials factor="PASSCODE" passcode="123456"/>
   </auth>
   


**Example: Authenticate with multi-factor authentication credentials HTTP request header: JSON**


.. code::

   POST /v2.0/tokens HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Content-Type: application/json
   Accept: application/json
   X-SessionId: APU9ymNjSKJG21HVdiRdOg0rk2fqh7uQ1FafVDXo3SId6nMHjUkKSDacFwDLGCC9U_DKI6Lwzu-wMi3LIWT-bA24EdGYdycM3rKzAfVPiCCjigN315ZLJo5s2TmiGQTSW9b5H7euQjJ6KBTk5elT2l8HrPH-9rrBjw


**Example: Authenticate with multi-factor authentication credentials request: JSON**
   
   {
   "auth": {
   "RAX-AUTH:passcodeCredentials": {
   "passcode":”123456"
   }
   }
   }


Response
""""""""""""""""

**Example: Authenticate with multi-factor authentication credentials: XML response with header**


.. code::

   < HTTP/1.1 200 OK
   < Vary:  Accept, Accept-Encoding, X-Auth-Token
   < Content-Type: application/xml
   < Content-Length: 387
   < Server: Jetty(6.1.25)

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
   
**Example: Authenticate with multi-factor authentication credentials: JSON response with header**


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




