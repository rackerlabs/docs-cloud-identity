=============================================================================
Get Service Apis -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Get Service Apis
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_get_service_apis_v2.0_rax-auth_service-apis.rst#request>`__
`Response <GET_get_service_apis_v2.0_rax-auth_service-apis.rst#response>`__

.. code-block:: javascript

    GET /v2.0/RAX-AUTH/service-apis

Gets a list of service APIs.



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





**Example Get Service Apis: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <serviceApis
         xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
         xmlns:atom="http://www.w3.org/2005/Atom" xmlns:identity="http://docs.openstack.org/identity/api/v2.0">
         <serviceApi type="compute" version="1.0"/>
         <serviceApi type="compute" version="2.0"/>
         <serviceApi type="object-store" version="2.0"/>
         <serviceApi type="rax:customer" version="1"/>
    </serviceApis>
    


**Example Get Service Apis: JSON request**


.. code::

    {
      "RAX-AUTH:serviceApis": [
        {
          "type": "compute",
          "version": "1.0"
        },
        {
          "type": "compute",
          "version": "2.0"
        },
        {
          "type": "object-store",
          "version": "2.0"
        },
        {
          "type": "rax:customer",
          "version": "1"
        }
      ]
    }

