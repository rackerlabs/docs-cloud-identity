
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _post-add-service-v2.0-os-ksadm-services:

Add service
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /v2.0/OS-KSADM/services

Adds a service.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|201                       |Created                  |The request has been     |
|                          |                         |fulfilled. The service   |
|                          |                         |has been added.          |
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
|X-Auth-Token              |String *(Required)*      |You need a valid admin   |
|                          |                         |token for access.        |
+--------------------------+-------------------------+-------------------------+





This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|name                      |String *(Required)*      |A service name.          |
+--------------------------+-------------------------+-------------------------+
|id                        |String *(Required)*      |A unique id to identify  |
|                          |                         |the service.             |
+--------------------------+-------------------------+-------------------------+
|type                      |String *(Required)*      |The type of service you  |
|                          |                         |are adding, ``Compute``, |
|                          |                         |for example.             |
+--------------------------+-------------------------+-------------------------+
|description               |String *(Optional)*      |A human-readable         |
|                          |                         |description for the      |
|                          |                         |service.                 |
+--------------------------+-------------------------+-------------------------+





**Example Add service: XML request**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   
   <service xmlns="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
   	id="123" name="nova" type="compute" description="OpenStack Compute Service" />
   





**Example Add service: JSON request**


.. code::

   {
       "OS-KSADM:service":{
           "id":"123",
           "name":"nova",
           "type":"compute",
           "description":"OpenStack Compute Service"
       }
   }





Response
""""""""""""""""










**Example Add service: XML response**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   
   <service xmlns="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
   	id="123" name="nova" type="compute" description="OpenStack Compute Service" />
   





**Example Add service: JSON response**


.. code::

   {
       "OS-KSADM:service":{
           "id":"123",
           "name":"nova",
           "type":"compute",
           "description":"OpenStack Compute Service"
       }
   }




