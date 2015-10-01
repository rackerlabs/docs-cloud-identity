
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-get-detailed-policy-content-v2.0-rax-auth-policies-policyid-blob-detail:

Get detailed policy content
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v2.0/RAX-AUTH/policies/{policyId}/blob_detail

Retrieves a policy content. 

The representation of the policy is different from the author's perspective and the policy enforcer's perspective. This API is intended for policy enforcers; it gives clear, fully detailed, non-verbose descriptions of the policy. 



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
|                          |                         |token.                   |
+--------------------------+-------------------------+-------------------------+
|{policyId}                |String *(Required)*      |A policy ID              |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




Response
""""""""""""""""










**Example Get detailed policy content: XML response**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <policy xmlns="http://docs.rackspace.com/identity/policy/v1.0">
        <rule>
             <subject roles="default"/>
             <capabilities serviceType="compute" version="2.0">
                  <capability action="GET" id="2378237"
                       name="create-server" url="/servers"/>
                  <capability action="GET" id="545454" name="get_servers" url="/servers"/>
                  <capability action="GET" id="23892323" name="get_server" url="/servers/{serverId}"/>
                  <capability action="PUT" id="10920192"
                       name="update-server" url="/servers/{serverId}"/>
                  <capability action="POST" id="272738723"
                       name="stop-server" url="/servers/{serverId}/stop"/>
             </capabilities>
        </rule>
        <rule>
             <subject id="jbryce"/>
             <capabilities serviceType="compute" version="2.0">
                  <capability action="GET" id="23892323" name="get_server" url="/servers/{serverId}">
                       <attribute name="tenantId" value="5473"/>
                       <attribute name="tenantId" value="99999"/>
                  </capability>
             </capabilities>
             <capabilities serviceType="swift" version="2.0">
                  <capability action="GET" id="378343" name="get-file" url="/containers/{containerId}/{filename}"/>
             </capabilities>
        </rule>
   </policy>
   




