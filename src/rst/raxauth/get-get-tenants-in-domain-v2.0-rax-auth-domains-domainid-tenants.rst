
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-get-tenants-in-domain-v2.0-rax-auth-domains-domainid-tenants:

Get tenants in domain
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v2.0/RAX-AUTH/domains/{domainId}/tenants

Lists tenants in a domain. 

Tenants can be used to create logical organization within a domain. For example, an entertainment business might use two tenants to separately identify resources related to two kinds of activity: manage Star Wars games and manage Star Wars pictures.



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





This operation does not accept a request body.




Response
""""""""""""""""










**Example Get tenants in domain: XML response**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <tenants xmlns="http://docs.openstack.org/identity/api/v2.0"
        xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0" xmlns:atom="http://www.w3.org/2005/Atom">
        <tenant display-name="Star Wars" enabled="true" id="5784574" name="star_wars">
             <description>Used to manage the Star Wars games</description>
        </tenant>
        <tenant display-name="Star Wars" enabled="true" id="Mosso_73843_FS" name="star_wars_pictures">
             <description>Used to manage the pictures for Star Wars</description>
        </tenant>
   </tenants>





**Example Get tenants in domain: JSON response**


.. code::

   {
       "tenants": [
           {
               "id": "5784574",
               "enabled": true,
               "display-name": "Star Wars",
               "description": "Used to manage the Star Wars games",
               "name": "star_wars"
           },
           {
               "id": "Mosso_73843_FS",
               "enabled": true,
               "display-name": "Star Wars",
               "description": "Used to manage the pictures for Star Wars",
               "name": "star_wars_pictures"
           }
       ]
   }




