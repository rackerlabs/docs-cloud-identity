.. _get-list-tenants-v2.0:

List tenants
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /v2.0/tenants

Get a list of tenants, or look up a tenant by name.

Identity administrators can use this operation to retrieve a list of tenants or 
an individual tenant by name.



This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |The request completed    |
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
""""""""""""""""

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|name                      |String *(Required)*      |The name of the tenant.  |
+--------------------------+-------------------------+-------------------------+
|X-Auth-Token              |String *(Required)*      |A valid authentication   |
|                          |                         |token issued to a user   |
|                          |                         |with administrative      |
|                          |                         |privileges.              |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.




Response
""""""""""""""""

This table shows the body parameters for the response:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|tenants                   |String                   |The tenants object       |
|                          |                         |returns the collection of|
|                          |                         |tenant resources that    |
|                          |                         |the authenticated user   |
|                          |                         |has permission to view.  |
+--------------------------+-------------------------+-------------------------+
|tenants.**tenant**        |                         |The tenant object        |
|                          |                         |returns the following    |
|                          |                         |tenant account           |
|                          |                         |information: name,       |
|                          |                         |tenant id, account       |
|                          |                         |status, and description. |
+--------------------------+-------------------------+-------------------------+
|tenants.**id**            |String *(Required)*      |The unique,              |
|                          |                         |system-generated ID      |
|                          |                         |that identifies the      |
|                          |                         |in the Rackspace system. |
+--------------------------+-------------------------+-------------------------+
|tenant.**name**           |String *(Required)*      |The answer that the user |
|                          |                         |can provide to verify an |
|                          |                         |account.                 |
+--------------------------+-------------------------+-------------------------+
|tenant.**description**    |String                   |Describes the tenant     |
|                          |                         |tenant account.          |
+--------------------------+-------------------------+-------------------------+
|tenant.**enabled**        |Boolean                  |Indicates whether the    |
|                          |                         |tenant is currently      |
|                          |                         |active for use with the  |
|                          |                         |Rackspace Cloud.         |
+--------------------------+-------------------------+-------------------------+



**Example:  List tenants response XML**


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
   



**Example:  List tenants response JSON**


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




