
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-get-users-in-domain-v2.0-rax-auth-domains-domainid-users:

Get users in domain
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v2.0/RAX-AUTH/domains/{domainId}/users

Lists users in a domain.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |The request succeeded.   |
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
|X-Auth-Token              |String *(Required)*      |A valid authentication   |
|                          |                         |token                    |
+--------------------------+-------------------------+-------------------------+
|{domainId}                |String *(Required)*      |A domain ID.             |
+--------------------------+-------------------------+-------------------------+



This table shows the query parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|enabled                   |String                   |A Boolean value that     |
|                          |                         |filters the list of      |
|                          |                         |tenants based on account |
|                          |                         |status. Specify          |
|                          |                         |``enabled=true`` to list |
|                          |                         |active (enabled)         |
|                          |                         |tenants; specify         |
|                          |                         |``enabled=false`` to     |
|                          |                         |list inactive tenants.   |
+--------------------------+-------------------------+-------------------------+




This operation does not accept a request body.




Response
""""""""""""""""










**Example Get users in domain: XML response**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <users xmlns="http://docs.openstack.org/identity/api/v2.0"
        xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0" 
        xmlns:atom="http://www.w3.org/2005/Atom">
        <user email="john.smith@example.org" enabled="true" id="123456" username="jqsmith"/>
        <user email="mike.turner@example.org" enabled="true" id="388493" username="miketurner"/>
        <user email="poe.joe@example.org" enabled="false" id="938439" username="poejo"/>
   </users>





**Example Get users in domain: JSON response**


.. code::

   {
     "users": [
       {
         "id": "123456",
         "enabled": true,
         "username": "jqsmith",
         "email": "john.smith@example.org"
       },
       {
         "id": "388493",
         "enabled": true,
         "username": "miketurner",
         "email": "mike.turner@example.org"
       },
       {
         "id": "938439",
         "enabled": false,
         "username": "poejo",
         "email": "poe.joe@example.org"
       }
     ]
   }




