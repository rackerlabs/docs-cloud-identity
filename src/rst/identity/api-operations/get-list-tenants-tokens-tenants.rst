
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-list-tenants-tokens-tenants:

List Tenants
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /tokens/tenants

Lists tenants.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |                         |The name is a unique     |
|                          |                         |string assigned to a     |
|                          |                         |tenant. The value can be |
|                          |                         |changed. A unique string |
|                          |                         |that identifies the      |
|                          |                         |tenant. Typically, the   |
|                          |                         |value comes from the     |
|                          |                         |back-end data store. The |
|                          |                         |tenant is a persistent   |
|                          |                         |value assigned when a    |
|                          |                         |tenant is created. The   |
|                          |                         |value cannot be          |
|                          |                         |modified. A free text    |
|                          |                         |description of the       |
|                          |                         |tenant. A boolean value  |
|                          |                         |that indicates whether   |
|                          |                         |the tenant is enabled. A |
|                          |                         |user, process, or        |
|                          |                         |application can only     |
|                          |                         |authenticate if the      |
|                          |                         |tenant associated with   |
|                          |                         |their account is         |
|                          |                         |enabled. A free text     |
|                          |                         |description of the       |
|                          |                         |tenant.                  |
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
|limit                     |Int *(Optional)*         |The page size.           |
+--------------------------+-------------------------+-------------------------+
|marker                    |String *(Optional)*      |The ID of the last item  |
|                          |                         |in the previous list.    |
+--------------------------+-------------------------+-------------------------+
|X-Auth-Token              |String *(Required)*      |A valid authentication   |
|                          |                         |token.                   |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




**Example List Tenants: JSON request**


.. code::

   GET /v2.0/tenants HTTP/1.1
   Host: auth.api.rackspacecloud.com
   Content-Type: application/json
   X-Auth-Token: fa8426a0-8eaf-4d22-8e13-7c1b16a9370c
   Accept: application/json





**Example List Tenants: XML request**


.. code::

   GET /v2.0/tenants HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/xml
   X-Auth-Token: eaaafd18-0fed-4b3a-81b4-663c99ec1cbb





Response
""""""""""""""""





This table shows the body parameters for the response:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|name                      |String *(Required)*      |The name is a unique     |
|                          |                         |string assigned to a     |
|                          |                         |tenant. The value can be |
|                          |                         |changed.                 |
+--------------------------+-------------------------+-------------------------+
|id                        |String *(Optional)*      |A unique string that     |
|                          |                         |identifies the tenant.   |
|                          |                         |Typically, the value     |
|                          |                         |comes from the back-end  |
|                          |                         |data store. The tenant   |
|                          |                         |is a persistent value    |
|                          |                         |assigned when a tenant   |
|                          |                         |is created. The value    |
|                          |                         |cannot be modified.      |
+--------------------------+-------------------------+-------------------------+
|description               |String *(Optional)*      |A free text description  |
|                          |                         |of the tenant.           |
+--------------------------+-------------------------+-------------------------+
|enabled                   |Boolean *(Optional)*     |A boolean value that     |
|                          |                         |indicates whether the    |
|                          |                         |tenant is enabled. A     |
|                          |                         |user, process, or        |
|                          |                         |application can only     |
|                          |                         |authenticate if the      |
|                          |                         |tenant associated with   |
|                          |                         |their account is enabled.|
+--------------------------+-------------------------+-------------------------+
|description               |String *(Optional)*      |A free text description  |
|                          |                         |of the tenant.           |
+--------------------------+-------------------------+-------------------------+







**Example List Tenants: JSON response**


.. code::

   {
       "tenants":[{
               "id":"1234",
               "name":"ACME Corp",
               "description":"A description ...",
               "enabled": true
           },
           {
               "id":"3456",
               "name":"Iron Works",
               "description":"A description ...",
               "enabled": true
           }
       ],
       "tenants_links":[]
   }





**Example List Tenants: XML response**


.. code::

   HTTP/1.1 200 OK
   Content-Type: application/xml; charset=UTF-8
   Content-Length: 200
   Date: Sun, 1 Jan 2011 9:00:00 GMT
   
   <?xml version="1.0" encoding="UTF-8"?>
   <tenants xmlns="http://docs.openstack.org/identity/api/v2.0">
       <tenant enabled="true" id="1234" name="ACME Corp">
           <description>A description...</description>
       </tenant>
       <tenant enabled="true" id="3645" name="Iron Works">
           <description>A description...</description>
       </tenant>
   </tenants>
   




