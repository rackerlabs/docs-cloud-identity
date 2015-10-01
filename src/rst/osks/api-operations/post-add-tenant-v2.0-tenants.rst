
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _post-add-tenant-v2.0-tenants:

Add tenant
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /v2.0/tenants

Creates a tenant.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|201                       |Created                  |The request has been     |
|                          |                         |fulfilled. The tenant    |
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





This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|tenantId                  |Uuid *(Optional)*        |Specify a unique ID for  |
|                          |                         |the tenant account.      |
+--------------------------+-------------------------+-------------------------+
|name                      |String *(Required)*      |Specify a unique name    |
|                          |                         |for the tenant account.  |
+--------------------------+-------------------------+-------------------------+
|enabled                   |Boolean *(Optional)*     |A Boolean value that     |
|                          |                         |determines whether the   |
|                          |                         |tenant account is        |
|                          |                         |active. Specify          |
|                          |                         |``enabled="true"`` or    |
|                          |                         |``enabled="false"``.     |
+--------------------------+-------------------------+-------------------------+
|description               |String *(Optional)*      |A human-readable string  |
|                          |                         |that provides            |
|                          |                         |information about the    |
|                          |                         |tenant account.          |
+--------------------------+-------------------------+-------------------------+





**Example Add tenant: XML request**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <tenant xmlns="http://docs.openstack.org/identity/api/v2.0"
           enabled="true" name="ACME Corp">
       <description>A description...</description>
   </tenant>
   





**Example Add tenant: JSON request**


.. code::

   {
     "tenant": {
       "name": "ACME corp",
       "description": "A description ...",
       "enabled": true
     }
   }
   





Response
""""""""""""""""










**Example Add tenant: XML response**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <tenant xmlns="http://docs.openstack.org/identity/api/v2.0"
           enabled="true" id="1234" name="ACME Corp">
       <description>A description...</description>
   </tenant>
   





**Example Add tenant: JSON response**


.. code::

   {
     "tenant": {
       "id": "1234",
       "name": "ACME corp",
       "description": "A description ...",
       "enabled": true
     }
   }
   




