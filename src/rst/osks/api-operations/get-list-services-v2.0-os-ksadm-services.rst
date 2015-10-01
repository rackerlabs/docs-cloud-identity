
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-list-services-v2.0-os-ksadm-services:

List services
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v2.0/OS-KSADM/services

Lists services.

List services.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200 203                   |OK                       |Request completed        |
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
|X-Auth-Token              |String *(Required)*      |You need a valid admin   |
|                          |                         |token for access.        |
+--------------------------+-------------------------+-------------------------+
|name                      |String *(Required)*      |A service name.          |
+--------------------------+-------------------------+-------------------------+



This table shows the query parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|marker                    |String *(Optional)*      |Allows us to page        |
|                          |                         |through list of users.   |
|                          |                         |This is the numeric id   |
|                          |                         |of the item to start the |
|                          |                         |list.                    |
+--------------------------+-------------------------+-------------------------+
|limit                     |Int *(Optional)*         |Allows us to set size of |
|                          |                         |page when paging through |
|                          |                         |list of users. This is   |
|                          |                         |the number of items per  |
|                          |                         |page.                    |
+--------------------------+-------------------------+-------------------------+




This operation does not accept a request body.




Response
""""""""""""""""










**Example List services: XML response**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   
   <services xmlns="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0">
     <service id="123" name="nova" type="compute" description="Openstack Compute Service" />
     <service id="234" name="glance" type="image" description="Openstack Image Service" />
   </services>





**Example List services: JSON response**


.. code::

   {
       "OS-KSADM:services":[{
               "id":"123",
               "name":"nova",
               "type":"compute",
               "description":"OpenStack Compute Service"
           },
           {
               "id":"234",
               "name":"glance",
               "type":"image",
               "description":"OpenStack Image Service"
           }
       ],
       "OS-KSADM:services_links":[]
   }




