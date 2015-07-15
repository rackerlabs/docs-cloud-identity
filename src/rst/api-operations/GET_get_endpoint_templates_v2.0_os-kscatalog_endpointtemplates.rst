=============================================================================
Get Endpoint Templates -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Get Endpoint Templates
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_get_endpoint_templates_v2.0_os-kscatalog_endpointtemplates.rst#request>`__
`Response <GET_get_endpoint_templates_v2.0_os-kscatalog_endpointtemplates.rst#response>`__

.. code-block:: javascript

    GET /v2.0/OS-KSCATALOG/endpointTemplates

Get users in a domain.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|                          |OK                       |The request succeeded.   |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |The request is missing   |
|                          |                         |one or more elements, or |
|                          |                         |the values of            |
|                          |                         |someelements are invalid.|
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
|                          |                         |requested                |
|                          |                         |resource.Submit a        |
|                          |                         |request to your account  |
|                          |                         |administrator to         |
|                          |                         |determine how to gain    |
|                          |                         |access.                  |
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
|404                       |Not Found                |The requested resource   |
|                          |                         |was not found.           |
+--------------------------+-------------------------+-------------------------+


Request
^^^^^^^^^^^^^^^^^

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|X-Auth-Token              |string *(Required)*      |A valid authentication   |
|                          |                         |token                    |
+--------------------------+-------------------------+-------------------------+








Response
^^^^^^^^^^^^^^^^^^





**Example Get Endpoint Templates: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <endpointTemplates
         xmlns="http://docs.openstack.org/identity/api/ext/OS-KSCATALOG/v1.0" xmlns:atom="http://www.w3.org/2005/Atom">
         <endpointTemplate
              adminURL="https://dfw.servers.api.rackspacecloud.com/v2/2882983"
              id="4"
              internalURL="https://dfw.servers.api.rackspacecloud.com/v2/2882983"
              name="cloudServersOpenStack"
              publicURL="https://dfw.servers.api.rackspacecloud.com/v2/2882983"
              region="DFW" type="compute">
              <version id="1"
                   info="https://dfw.servers.api.rackspacecloud.com/v2" list="https://dfw.servers.api.rackspacecloud.com"/>
         </endpointTemplate>
         <endpointTemplate id="5"
              internalURL="https://storage101.ord1.clouddrive.com/v1/MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee"
              name="cloudFiles"
              publicURL="https://storage101.ord1.clouddrive.com/v1/MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee"
              region="IAD" type="object-store">
              <version id="1"
                   info="https://storage101.ord1.clouddrive.com/v1" list="https://storage101.ord1.clouddrive.com"/>
         </endpointTemplate>
    </endpointTemplates>
    


**Example Get Endpoint Templates: JSON request**


.. code::

    {
      "OS-KSCATALOG:endpointTemplates": [
        {
          "region": "DFW",
          "id": "4",
          "publicURL": "https://dfw.servers.api.rackspacecloud.com/v2/2882983",
          "name": "cloudServersOpenStack",
          "adminURL": "https://dfw.servers.api.rackspacecloud.com/v2/2882983",
          "type": "compute",
          "versionId": "1",
          "versionList": "https://dfw.servers.api.rackspacecloud.com",
          "versionInfo": "https://dfw.servers.api.rackspacecloud.com/v2",
          "internalURL": "https://dfw.servers.api.rackspacecloud.com/v2/2882983"
        },
        {
          "region": "IAD",
          "id": "5",
          "publicURL": "https://storage101.ord1.clouddrive.com/v1/MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee",
          "name": "cloudFiles",
          "type": "object-store",
          "versionId": "1",
          "versionList": "https://storage101.ord1.clouddrive.com",
          "versionInfo": "https://storage101.ord1.clouddrive.com/v1",
          "internalURL": "https://storage101.ord1.clouddrive.com/v1/MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee"
        }
      ]
    }

