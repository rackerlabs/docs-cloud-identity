
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-list-endpoints-for-token-v2.0-tokens-tokenid-endpoints:

List endpoints for token
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v2.0/tokens/{tokenId}/endpoints

Return a list of endpoints associated with a specific token. 

This call returns a list of endpoints associated with a specific token. Like the service catalog returned by a successful authentication, you can use this list of endpoints as the basis of a list of the services available to this user. 

For more information and examples, see `"Sample Authentication Request and Response" <http://docs.rackspace.com/auth/api/v2.0/auth-client-devguide/content/Sample_Request_Response-d1e64.html>`__.



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
|{tokenId}                 |String *(Required)*      |The unique               |
|                          |                         |authentication token ID  |
|                          |                         |for the token to be      |
|                          |                         |revoked.                 |
+--------------------------+-------------------------+-------------------------+
|X-Auth-Token              |String *(Required)*      |A valid authentication   |
|                          |                         |token with               |
|                          |                         |administrative access.   |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




Response
""""""""""""""""










**Example List endpoints for token: JSON response**


.. code::

   {
       "endpoints":[{
                   "id":1,
                   "tenantId":"1",
                   "region":"North",
                   "name": "Compute",
                   "type":"compute",
                   "publicURL":"https://compute.north.public.com/v1",
                   "internalURL":"https://compute.north.internal.com/v1",
                   "adminURL" : "https://compute.north.internal.com/v1",
                   "versionId":"1",
                   "versionInfo":"https://compute.north.public.com/v1/",
                   "versionList":"https://compute.north.public.com/"
               },
               {
                   "id":2,
                   "tenantId":"1",
                   "region":"South",
                    "name": "Compute",
                   "type":"compute",
                   "publicURL":"https://compute.north.public.com/v1",
                   "internalURL":"https://compute.north.internal.com/v1",
                   "adminURL" : "https://compute.north.internal.com/v1",
                   "versionId":"1",
                   "versionInfo":"https://compute.north.public.com/v1/",
                   "versionList":"https://compute.north.public.com/"
               },
               {
                   "id":3,
                   "tenantId":"1",
                   "region":"East",
                   "name": "Compute",
                   "type":"compute",
                   "publicURL":"https://compute.north.public.com/v1",
                   "internalURL":"https://compute.north.internal.com/v1",
                   "adminURL" : "https://compute.north.internal.com/v1",
                   "versionId":"1",
                   "versionInfo":"https://compute.north.public.com/v1/",
                   "versionList":"https://compute.north.public.com/"
               },
               {
                   "id":4,
                   "tenantId":"1",
                   "region":"West",
                    "name": "Compute",
                   "type":"compute",
                   "publicURL":"https://compute.north.public.com/v1",
                   "internalURL":"https://compute.north.internal.com/v1",
                   "adminURL" : "https://compute.north.internal.com/v1",
                   "versionId":"1",
                   "versionInfo":"https://compute.north.public.com/v1/",
                   "versionList":"https://compute.north.public.com/"
               },
               {
                   "id":5,
                   "tenantId":"1",
                   "region":"Global",
                    "name": "Compute",
                   "type":"compute",
                   "publicURL":"https://compute.north.public.com/v1",
                   "internalURL":"https://compute.north.internal.com/v1",
                   "adminURL" : "https://compute.north.internal.com/v1",
                   "versionId":"1",
                   "versionInfo":"https://compute.north.public.com/v1/",
                   "versionList":"https://compute.north.public.com/"
               }
           ],
       "endpoints_links":[]
   }





**Example List endpoints for token: XML response**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   
   <endpoints
       xmlns="http://docs.openstack.org/identity/api/v2.0">
     <endpoint
         id="1" 
         tenantId="1"
         name="Compute"
         type="compute"
         region="North"
         publicURL="https://compute.north.public.com/v1"
         internalURL="https://compute.north.internal.com/v1"
         adminURL="https://compute.north.internal.com/v1">
         <version
             id="1"
             info="https://compute.north.public.com/v1/"
             list="https://compute.north.public.com/"
         />
     </endpoint>
     <endpoint
         id="2" 
         tenantId="2"
         name="Compute"
         type="compute"
         region="South"
         publicURL="https://compute.north.public.com/v1"
         internalURL="https://compute.north.internal.com/v1"
         adminURL="https://compute.north.internal.com/v1">
         <version
             id="1"
             info="https://compute.north.public.com/v1/"
             list="https://compute.north.public.com/"
         />
     </endpoint>
     <endpoint
         id="3" 
         tenantId="1"
         name="Compute"
         type="compute"
         region="East"
         publicURL="https://compute.north.public.com/v1"
         internalURL="https://compute.north.internal.com/v1"
         adminURL="https://compute.north.internal.com/v1"
         tenantId="1"
     />
     <endpoint
         id="4" 
         tenantId="1"
         name="Compute"
         type="compute"
         region="West"
         publicURL="https://compute.north.public.com/v1"
         internalURL="https://compute.north.internal.com/v1"
         adminURL="https://compute.north.internal.com/v1">
         <version
             id="1"
             info="https://compute.north.public.com/v1/"
             list="https://compute.north.public.com/"
         />
     </endpoint>
     <endpoint
         id="5" 
         tenantId="1"
         name="Compute"
         type="compute"
         region="Global"
         publicURL="https://compute.north.public.com/v1"
         internalURL="https://compute.north.internal.com/v1"
         adminURL="https://compute.north.internal.com/v1">
         <version
             id="1"
             info="https://compute.north.public.com/v1/"
             list="https://compute.north.public.com/"
         />
     </endpoint>
   </endpoints>
   




