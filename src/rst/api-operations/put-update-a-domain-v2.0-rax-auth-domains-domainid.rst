
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _put-update-a-domain-v2.0-rax-auth-domains-domainid:

Update a domain
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    PUT /v2.0/RAX-AUTH/domains/{domainId}

Updates domain attributes.

When you submit the update request, include only the parameter values that you want to update. Administrators can change the multi-factor authentication domain enforcement setting by using the `Update multi-factor authentication domain settings operation. <PUT_updateDomainMultiFactorEnforcement_v2.0_RAX-AUTH_domains__domainId__multi-factor_Multifactor_Calls.html>`__.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|204                       |No content               |The request succeeded.   |
|                          |                         |The server fulfilled the |
|                          |                         |request but does not     |
|                          |                         |need to return a body.   |
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
|X-Auth-Token              |String *(Required)*      |A valid authentication   |
|                          |                         |token                    |
+--------------------------+-------------------------+-------------------------+
|{domainId}                |String *(Required)*      |A domain ID.             |
+--------------------------+-------------------------+-------------------------+





This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|RAX-AUTH:domain           |Object *(Required)*      |Object to specify these  |
|                          |                         |domain configuration     |
|                          |                         |settings: ``id``,        |
|                          |                         |``enabled``, ``name``.   |
+--------------------------+-------------------------+-------------------------+
|name                      |String *(Required)*      |The domain name.         |
+--------------------------+-------------------------+-------------------------+
|enabled                   |Boolean *(Optional)*     |Set to true to enable    |
|                          |                         |the domain. Otherwise,   |
|                          |                         |set to false.            |
+--------------------------+-------------------------+-------------------------+
|rax-auth:description      |String *(Optional)*      |The domain description.  |
+--------------------------+-------------------------+-------------------------+





**Example Update a domain: XML request**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <rax-auth:domain enabled="false"
        xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
        xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
        xmlns:atom="http://www.w3.org/2005/Atom" 
        xmlns:identity="http://docs.openstack.org/identity/api/v2.0">
   </rax-auth:domain>





**Example Update a domain: JSON request**


.. code::

   {
     "RAX-AUTH:domain": {
       "enabled": true,
     }
   }





Response
""""""""""""""""










**Example 204 success respone**


.. code::

   HTTP/1.1 204 No Content
   


This operation does not return a response body.



