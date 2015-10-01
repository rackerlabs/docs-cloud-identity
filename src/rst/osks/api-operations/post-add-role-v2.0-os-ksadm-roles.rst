
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _post-add-role-v2.0-os-ksadm-roles:

Add role
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /v2.0/OS-KSADM/roles

Adds a role.

Identity administrators can use this operation to add a role to manage service access (with user-assigned Rackspace capabilities), allowing the customer to tailor user roles to his or her business needs.

.. note::
   Roles added by this call are by default visible to customers. If you would like the role to be service-managed or visible only to services, please open a NEB ticket for Cloud Nebulous Operations using `https://jira.mosso.com <https://jira.mosso.com>`__
   
   



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|201                       |Created                  |The request has been     |
|                          |                         |fulfilled. The role has  |
|                          |                         |been added.              |
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
|name                      |String *(Required)*      |The name of the role.    |
+--------------------------+-------------------------+-------------------------+
|id                        |String *(Optional)*      |A role id.               |
+--------------------------+-------------------------+-------------------------+
|description               |String *(Optional)*      |Additional information   |
|                          |                         |about the role to help   |
|                          |                         |administrators and users |
|                          |                         |understand its scope and |
|                          |                         |purpose.                 |
+--------------------------+-------------------------+-------------------------+
|serviceId                 |String *(Optional)*      |Additional information   |
|                          |                         |about the role to help   |
|                          |                         |administrators and users |
|                          |                         |understand its scope and |
|                          |                         |purpose.                 |
+--------------------------+-------------------------+-------------------------+
|tenantId                  |Uuid *(Optional)*        |If the role is intended  |
|                          |                         |for use with a specific  |
|                          |                         |tenant, and the tenant   |
|                          |                         |Id has not been defined, |
|                          |                         |use this attribute to    |
|                          |                         |specify a unique ID for  |
|                          |                         |the tenant.              |
+--------------------------+-------------------------+-------------------------+





**Example Add role: XML request**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   
   <role xmlns="http://docs.openstack.org/identity/api/v2.0"
     id="123" name="Admin" description="All Access" serviceId="abc4321ebabeeabb70a0e702a4626977c331d5c4" />
   





**Example Add role: JSON request**


.. code::

   {
     "role": {
       "id": "123",
       "name": "Guest",
       "description": "Guest Access"
     }
   }
   





Response
""""""""""""""""










**Example Add role: XML response**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   
   <role xmlns="http://docs.openstack.org/identity/api/v2.0"
     id="123" name="Admin" description="All Access" serviceId="abc4321ebabeeabb70a0e702a4626977c331d5c4" />
   





**Example Add role: JSON response**


.. code::

   {
     "role": {
       "id": "123",
       "name": "Guest",
       "description": "Guest Access"
     }
   }
   




