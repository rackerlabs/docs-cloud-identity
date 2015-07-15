=============================================================================
Get Default Region Services -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Get Default Region Services
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_get_default_region_services_v2.0_rax-auth_default-region_services.rst#request>`__
`Response <GET_get_default_region_services_v2.0_rax-auth_default-region_services.rst#response>`__

.. code-block:: javascript

    GET /v2.0/RAX-AUTH/default-region/services

Retrieves the list of services that restrict the default regions that users can specify.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |The request succeeded.   |
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





**Example Get Default Region Services: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <defaultRegionServices
         xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
         xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
         xmlns:atom="http://www.w3.org/2005/Atom" 
         xmlns:identity="http://docs.openstack.org/identity/api/v2.0">
         <serviceName>cloudFiles</serviceName>
         <serviceName>openstackNova</serviceName>
    </defaultRegionServices>


**Example Get Default Region Services: JSON request**


.. code::

    {
      "RAX-AUTH:defaultRegionServices": [
        "cloudFiles",
        "openstackNova"
      ]
    }

