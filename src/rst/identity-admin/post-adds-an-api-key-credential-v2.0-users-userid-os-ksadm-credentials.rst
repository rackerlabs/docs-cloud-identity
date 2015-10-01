
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _post-adds-an-api-key-credential-v2.0-users-userid-os-ksadm-credentials:

Adds an API key credential
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /v2.0/users/{userId}/OS-KSADM/credentials

Adds an API credential to a specified user account.

Identity administrators can update a user account to add an API credential.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|201                       |Created                  |The request completed    |
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




This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|X-Auth-Token              |String *(Required)*      |A valid admin            |
|                          |                         |authentication token.    |
+--------------------------+-------------------------+-------------------------+
|{userId}                  |String *(Required)*      |A user ID assigned by    |
|                          |                         |system when user is      |
|                          |                         |added.                   |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




**Example Adds an API key credential: XML request**


.. code::

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <apiKeyCredentials 
   	xmlns="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0" 
   	xmlns:ns2="http://www.w3.org/2005/Atom" 
   	xmlns:ns3="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0" 
   	xmlns:ns4="http://docs.openstack.org/identity/api/v2.0" 
   	xmlns:ns5="http://docs.rackspace.com/identity/api/ext/RAX-KSGRP/v1.0" 
   	xmlns:ns6="http://docs.rackspace.com/identity/api/ext/RAX-KSQA/v1.0" 
   	xmlns:ns7="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0" 
   	xmlns:ns8="http://docs.openstack.org/identity/api/ext/OS-KSEC2/v1.0" username="1406847123456" apiKey="cffeab0e6d0d472f84b5c20c70123456"/>





**Example Adds an API key credential: JSON request**


.. code::

   {
       "RAX-KSKEY:apiKeyCredentials": {
           "username": "1406847123456",
           "apiKey": "cffeab0e6d0d472f84b5c20c70123456"
       }
   }





Response
""""""""""""""""










**Example Adds an API key credential: XML response**


.. code::

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <apiKeyCredentials 
   	xmlns="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0" 
   	xmlns:ns2="http://www.w3.org/2005/Atom" 
   	xmlns:ns3="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0" 
   	xmlns:ns4="http://docs.openstack.org/identity/api/v2.0" 
   	xmlns:ns5="http://docs.rackspace.com/identity/api/ext/RAX-KSGRP/v1.0" 
   	xmlns:ns6="http://docs.rackspace.com/identity/api/ext/RAX-KSQA/v1.0" 
   	xmlns:ns7="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0" 
   	xmlns:ns8="http://docs.openstack.org/identity/api/ext/OS-KSEC2/v1.0" username="1406847123456" apiKey="cffeab0e6d0d472f84b5c20c70123456"/>





**Example Adds an API key credential: JSON response**


.. code::

   {
       "RAX-KSKEY:apiKeyCredentials": {
           "username": "1406847123456",
           "apiKey": "cffeab0e6d0d472f84b5c20c70123456"
       }
   }




