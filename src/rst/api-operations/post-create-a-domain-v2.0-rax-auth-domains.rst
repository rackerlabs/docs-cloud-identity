
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _post-create-a-domain-v2.0-rax-auth-domains:

Create a domain
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /v2.0/RAX-AUTH/domains

Creates a domain.

Clients must specify the domain ID in the request body.

Create domain cURL: JSON request in a cURL command

``$ curl -s $endpoint\2.0\domain \ -d '{"RAX-AUTH:domain": {"enabled":true,"id":"myDomainId","name":"newDomain"}}' \ -H "Content-type: application/json" \ -H "X-Auth-Token: $token \`` 



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|201                       |Created                  |The request has been     |
|                          |                         |fulfilled. The domain    |
|                          |                         |has been created.        |
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
|405                       |Invalid Method           |The method specified in  |
|                          |                         |the request is not valid |
|                          |                         |for the resource         |
|                          |                         |identified in the        |
|                          |                         |request URI.             |
+--------------------------+-------------------------+-------------------------+
|409                       |Conflict                 |The domain already       |
|                          |                         |exists.                  |
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





This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|RAX-AUTH:domain           |Object *(Required)*      |Object to specify these  |
|                          |                         |domain configuration     |
|                          |                         |settings: ``id``,        |
|                          |                         |``enabled``, ``name``.   |
+--------------------------+-------------------------+-------------------------+
|id                        |String *(Required)*      |The unique id for the    |
|                          |                         |domain.                  |
+--------------------------+-------------------------+-------------------------+
|name                      |String *(Required)*      |The domain name.         |
+--------------------------+-------------------------+-------------------------+
|enabled                   |Boolean *(Optional)*     |Set to true to enable    |
|                          |                         |the domain. Otherwise,   |
|                          |                         |set to false.            |
+--------------------------+-------------------------+-------------------------+
|rax-auth:description      |String *(Optional)*      |The domain description.  |
+--------------------------+-------------------------+-------------------------+





**Example Create a domain: XML request**


.. code::

   POST /v2.0/RAX-AUTH/domains/ HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/xml
   Content-type: application/xml
   X-Auth-Token: e681f3fffb9544bc9c46779442d12345


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <rax-auth:domain enabled="true" id="-222345" name="myNewDomain"
        xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
        xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
        xmlns:atom="http://www.w3.org/2005/Atom" 
        xmlns:identity="http://docs.openstack.org/identity/api/v2.0">
        <rax-auth:description>"A very good customer"</rax-auth:description>
   </rax-auth:domain>





**Example Create a domain: JSON request**


.. code::

   POST /v2.0/RAX-AUTH/domains/ HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/json
   Content-type: application/json
   X-Auth-Token: e681f3fffb9544bc9c46779442d12345


.. code::

   {
     "RAX-AUTH:domain": {
       "id": "222345",
       "enabled": true,
       "description": "A very good customer",
       "name": "myNewDomain"
     }
   }





Response
""""""""""""""""






This operation does not return a response body.




