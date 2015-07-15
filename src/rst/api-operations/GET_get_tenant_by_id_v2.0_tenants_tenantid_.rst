=============================================================================
Get Tenant By Id -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Get Tenant By Id
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_get_tenant_by_id_v2.0_tenants_tenantid_.rst#request>`__
`Response <GET_get_tenant_by_id_v2.0_tenants_tenantid_.rst#response>`__

.. code-block:: javascript

    GET /v2.0/tenants/{tenantId}

Returns information about a tenant, by ID.

This request returns the following information for the tenant with the specified ID: tenant's ID, name, description, and status.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |The request completed    |
|                          |                         |successfully.            |
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
|{tenantId}                |capi:UUID *(Required)*   |The unique ID assigned   |
|                          |                         |to the tenant account.   |
+--------------------------+-------------------------+-------------------------+
|X-Auth-Token              |xsd:string *(Required)*  |A valid authentication   |
|                          |                         |token issued to a user   |
|                          |                         |with administrative      |
|                          |                         |privileges.              |
+--------------------------+-------------------------+-------------------------+








Response
^^^^^^^^^^^^^^^^^^





**Example Get Tenant By Id: JSON request**


.. code::

    {
      "tenant": {
        "id": "1234",
        "name": "ACME corp",
        "description": "A description ...",
        "enabled": true
      }
    }
    


**Example Get Tenant By Id: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <tenant xmlns="http://docs.openstack.org/identity/api/v2.0"
            enabled="true" id="1234" name="ACME Corp">
        <description>A description...</description>
    </tenant>
    

