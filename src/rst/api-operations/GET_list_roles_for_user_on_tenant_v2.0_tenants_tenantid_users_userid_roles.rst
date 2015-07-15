=============================================================================
List Roles For User On Tenant -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

List Roles For User On Tenant
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_list_roles_for_user_on_tenant_v2.0_tenants_tenantid_users_userid_roles.rst#request>`__
`Response <GET_list_roles_for_user_on_tenant_v2.0_tenants_tenantid_users_userid_roles.rst#response>`__

.. code-block:: javascript

    GET /v2.0/tenants/{tenantId}/users/{userId}/roles

List roles for a specified user on a specified tenant.

This operation returns a list of roles for a specified user within a specified tenant. The list of roles excludes any global roles associated with this user.

Users and tenants are specified by their unique ID. If you do not know the tenant or user ID, you can use the Get user by name and Get tenant by name operations to retrieve the value.



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
|{userId}                  |xsd:string *(Required)*  |Specify the ID.          |
+--------------------------+-------------------------+-------------------------+
|{tenantId}                |UUID *(Required)*        |The unique ID assigned   |
|                          |                         |to the tenant account.   |
+--------------------------+-------------------------+-------------------------+
|                          |                         |A valid authentication   |
|                          |                         |token issued to a user   |
|                          |                         |with administrative      |
|                          |                         |privileges.              |
+--------------------------+-------------------------+-------------------------+








Response
^^^^^^^^^^^^^^^^^^





**Example List Roles For User On Tenant: JSON request**


.. code::

    {
        "roles": [
            {
                "description": "DevOps center",
                "id": "100",
                "name": "devops",
                "serviceId": "cke5372rw2rty8bb70a0e702a4626977x4406e5"
            },
            {
                "description": "Account creator public role",
                "id": "30007896",
                "name": "acctCreator:public",
                "serviceId": "cke5372ebabeeabb70a0e702a4626977x4406e5"
            },
            {
                "description": "Admin creator trusted role",
                "id": "30007897",
                "name": "acctCreator:trusted",
                "serviceId": "cke5372ebabeeabb70a0e702a4626977x4406e5"
            },
            {
                "description": "Admin role for database service",
                "id": "30007653",
                "name": "database:admin",
                "serviceId": "cke5372ebabeeabb70a0e702a4626977x4406e5"
            },
           
        ]
    }


**Example List Roles For User On Tenant: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8"?>
      <roles 
        xmlns:atom="http://www.w3.org/2005/Atom" 
        xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0" 
        xmlns="http://docs.openstack.org/identity/api/v2.0" 
        xmlns:ns4="http://docs.rackspace.com/identity/api/ext/RAX-KSGRP/v1.0" 
        xmlns:rax-ksqa="http://docs.rackspace.com/identity/api/ext/RAX-KSQA/v1.0" 
        xmlns:os-ksadm="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0" 
        xmlns:rax-kskey="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0" 
        xmlns:os-ksec2="http://docs.openstack.org/identity/api/ext/OS-KSEC2/v1.0">
        
        <role id="100" name="devops" description="DevOps center" serviceId="cke5372rw2rty8bb70a0e702a4626977x4406e5" rax-auth:propagate="true"/>
        <role id="30007896" name="acctCreator:public" description="Account creator public role" serviceId="cke5372ebabeeabb70a0e702a4626977x4406e5" rax-auth:propagate="false"/>
        <role id="30007897" name="acctCreator:trusted" description="Account creator trusted role" serviceId="bde1268ebabeeabb70a0e702a4626977c331d5c4" rax-auth:propagate="false"/>
        <role id="30007653" name="database:admin" description="admin role for cloud files" serviceId="bde1268ebabeeabb70a0e702a4626977c331d5c4" rax-auth:propagate="false"/> 
    </roles>
    
    

