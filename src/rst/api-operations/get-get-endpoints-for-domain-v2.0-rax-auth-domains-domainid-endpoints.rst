
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-get-endpoints-for-domain-v2.0-rax-auth-domains-domainid-endpoints:

Get endpoints for domain
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v2.0/RAX-AUTH/domains/{domainId}/endpoints

Get endpoints restricted to a domain. 

This operation returns a list of domain endpoints for which the supplied token provides access. If a token has access to a tenant that exists in the domain, then the token has access to the domain. If the token belongs to an admin user, a list of all domain endpoints may be returned. 



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










**Example Get endpoints for domain: XML response**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <endpoints xmlns="http://docs.openstack.org/identity/api/v2.0"
        xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0" xmlns:atom="http://www.w3.org/2005/Atom">
        <endpoint
             adminURL="https://dfw.servers.api.rackspacecloud.com/v2/2882983"
             id="4"
             internalURL="https://dfw.servers.api.rackspacecloud.com/v2/2882983"
             name="cloudServersOpenStack"
             publicURL="https://dfw.servers.api.rackspacecloud.com/v2/2882983"
             region="DFW" tenantId="2882983" type="compute">
             <version id="1"
                  info="https://dfw.servers.api.rackspacecloud.com/v2" list="https://dfw.servers.api.rackspacecloud.com"/>
        </endpoint>
        <endpoint id="5"
             internalURL="https://storage101.ord1.clouddrive.com/v1/MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee"
             name="cloudFiles"
             publicURL="https://storage101.ord1.clouddrive.com/v1/MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee"
             region="IAD"
             tenantId="MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee" type="objectStore">
             <version id="1"
                  info="https://storage101.ord1.clouddrive.com/v1" list="https://storage101.ord1.clouddrive.com"/>
        </endpoint>
   </endpoints>





**Example Get endpoints for domain: JSON response**


.. code::

   {
       "OS-KSCATALOG:endpoints": [
           {
               "tenantId": "2882983",
               "region": "DFW",
               "id": 4,
               "publicURL": "https://dfw.servers.api.rackspacecloud.com/v2/2882983",
               "name": "cloudServersOpenStack",
               "adminURL": "https://dfw.servers.api.rackspacecloud.com/v2/2882983",
               "type": "compute",
               "versionId": "1",
               "versionInfo": "https://dfw.servers.api.rackspacecloud.com/v2",
               "versionList": "https://dfw.servers.api.rackspacecloud.com"
           },
           {
               "tenantId": "MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee",
               "region": "IAD",
               "id": 5,
               "publicURL": "https://storage101.ord1.clouddrive.com/v1/MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee",
               "name": "cloudFiles",
               "type": "objectStore",
               "versionId": "1",
               "versionInfo": "https://storage101.ord1.clouddrive.com/v1",
               "versionList": "https://storage101.ord1.clouddrive.com",
               "internalURL": "https://storage101.ord1.clouddrive.com/v1/MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee"
           }
       ]
   }




