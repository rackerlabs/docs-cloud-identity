
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _put-update-capabilities-v2.0-rax-auth-service-apis-type-version-capabilities:

Update capabilities
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    PUT /v2.0/RAX-AUTH/service-apis/{type}/{version}/capabilities

Update the capabilities for a Service API. 

Any capabilities that previously existed for this endpoint template will be overridden. There will be future support to update capabilities by specifying a WADL as the payload. A WADL describes all the capabilities that can exist for a service. 



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
|{version}                 |String *(Required)*      |The service version, v1  |
|                          |                         |or v2.0 for example. >   |
+--------------------------+-------------------------+-------------------------+
|{type}                    |String *(Required)*      |The service type,        |
|                          |                         |compute, object-store,   |
|                          |                         |and rax-dns for example. |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




**Example Update capabilities: XML request**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <capabilities
        xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
        xmlns:identity="http://docs.openstack.org/identity/api/v2.0" xmlns:ns3="http://www.w3.org/2005/Atom">
        <capability action="GET" id="get_servers" name="get_servers" url="/servers"/>
        <capability action="GET" id="get_server" name="get_server" url="/servers/{serverId}"/>
        <capability action="POST" id="stop_server" name="stop_server" url="/servers/{serverId}/stop"/>
   </capabilities>
   





**Example Update capabilities: JSON request**


.. code::

   {
     "RAX-AUTH:capabilities": [
       {
         "id": "get_servers",
         "name": "get_servers",
         "action": "GET",
         "url": "/servers"
       },
       {
         "id": "get_server",
         "name": "get_server",
         "action": "GET",
         "url": "/servers/{serverId}"
       },
       {
         "id": "stop_server",
         "name": "stop_server",
         "action": "POST",
         "url": "/servers/{serverId}/stop"
       }
     ]
   }





Response
""""""""""""""""






This operation does not return a response body.




