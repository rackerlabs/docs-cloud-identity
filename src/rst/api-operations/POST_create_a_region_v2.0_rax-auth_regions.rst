=============================================================================
Create A Region -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Create A Region
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <POST_create_a_region_v2.0_rax-auth_regions.rst#request>`__
`Response <POST_create_a_region_v2.0_rax-auth_regions.rst#response>`__

.. code-block:: javascript

    POST /v2.0/RAX-AUTH/regions

Creates a region.

Clients must specify the region name in the request body.

Clients must specify whether or not the region is default in the request body. When a user is created, they are assigned the default region based on which region is set as ``“isDefault”:true``. This is used to assist Next Gen Compute capacity by suggesting to new users who they provision where we want them to. The user can change their default region through the update user API call, but they are restricted to changing it only to one of their regions listed in the service catalog for the CloudServersOpenStack service.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|201                       |Created                  |The request has been     |
|                          |                         |fulfilled. The region    |
|                          |                         |has been created.        |
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
|415                       |Bad Media Type           |Bad media type. This may |
|                          |                         |result if the wrong      |
|                          |                         |media type is used in    |
|                          |                         |the API request. Check   |
|                          |                         |the content-type and     |
|                          |                         |accept headers included  |
|                          |                         |in the request.          |
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








**Example Create A Region: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <region enabled="true" isDefault="true" name="DFW"
         xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
         xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
         xmlns:atom="http://www.w3.org/2005/Atom" 
         xmlns:identity="http://docs.openstack.org/identity/api/v2.0"/>


**Example Create A Region: JSON request**


.. code::

    {
      "RAX-AUTH:region": {
        "enabled": true,
        "isDefault": true,
        "name": "DFW"
      }
    }


Response
^^^^^^^^^^^^^^^^^^




