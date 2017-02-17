.. _get-lists-available-roles-to-manage-service-access-v2.0:

List roles for managing service access
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /v2.0/OS-KSADM/roles

Lists available roles for managing access to Rackspace Cloud services.

Use the List roles API operation to retrieve the available roles. The response
returns  the roles object with information about each role, including the id
for the service  that the role applies to.

If you use the limit and marker parameter, the previous and next links are in
the header.


This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |Request completed        |
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
-------

This table shows the header parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|X-Auth-Token              |Header                   |A valid admin            |
|                          |String *(Required)*      |authentication token.    |
+--------------------------+-------------------------+-------------------------+



This table shows the query parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|limit                     |Int *(Optional)*         |Requests a specified     |
|                          |                         |page size of returned    |
|                          |                         |items from the query.    |
|                          |                         |Returns a number of      |
|                          |                         |items up to the          |
|                          |                         |specified limit value.   |
|                          |                         |Use the ``limit``        |
|                          |                         |parameter to make an     |
|                          |                         |initial limited request  |
|                          |                         |and use the ID of the    |
|                          |                         |last-seen item from the  |
|                          |                         |response as the          |
|                          |                         |``marker`` parameter     |
|                          |                         |value in a subsequent    |
|                          |                         |limited request.         |
+--------------------------+-------------------------+-------------------------+
|marker                    |String *(Optional)*      |Specifies the ID of the  |
|                          |                         |last-seen item. Use the  |
|                          |                         |``limit`` parameter to   |
|                          |                         |make an initial limited  |
|                          |                         |request and use the ID   |
|                          |                         |of the last-seen item    |
|                          |                         |from the response as the |
|                          |                         |``marker`` parameter     |
|                          |                         |value in a subsequent    |
|                          |                         |limited request.         |
+--------------------------+-------------------------+-------------------------+


This operation does not accept a request body.


**Example:  Lists available roles to manage service access request: XML**

.. code::

   GET /v2.0/OS-KSADM/roles HTTP/1.1
   Host: identity.api.rackspacecloud.com
   X-Auth-Token:82994d2fb9a0483a85b6ba622c212345
   Accept: application/xml
   Content-type: application/xml


**Example:  Lists available roles to manage service access: JSON request**

.. code::

   GET /v2.0/OS-KSADM/roles HTTP/1.1
   Host: identity.api.rackspacecloud.com
   X-Auth-Token:82994d2fb9a0483a85b6ba622c2c4934
   Accept: application/json
   Content-type: application/json


Response
--------

This table shows the body parameters for the response:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|roles                     |String                   |Role object.             |
+--------------------------+-------------------------+-------------------------+
|roles.\ **id**            |Int                      |The role ID.             |
+--------------------------+-------------------------+-------------------------+
|roles.\ **name**          |String                   |The role name.           |
+--------------------------+-------------------------+-------------------------+
|roles.\ **description**   |String                   |The role description.    |
+--------------------------+-------------------------+-------------------------+
|roles.\ **serviceId**     |String                   |The id for the Rackspace |
|                          |                         |Cloud service to which   |
|                          |                         |the role applies.        |
+--------------------------+-------------------------+-------------------------+
|roles.\                   |Boolean *(Optional)*     |Indicates whether this   |
|**RAX-AUTH:propagate**    |                         |role is assigned to an   |
|                          |                         |account owner            |
|                          |                         |(identity:user-admin)    |
|                          |                         |and automatically        |
|                          |                         |inherited by all account |
|                          |                         |users (identity:default).|
+--------------------------+-------------------------+-------------------------+



**Example:  Lists available roles to manage service access: XML response**


.. code::

   HTTP/1.1 200 OK
   Content-Type: application/xml
   Content-Length: 3872
   Connection: keep-alive
   Link: <http://identity.api.rackspacecloud.com/cloud/v2.0/OS-KSADM/roles?marker=75&limit=25>; rel="last",
     <http://identity.api.rackspacecloud.com/cloud/v2.0/OS-KSADM/roles?marker=25&limit=25>; rel="next"


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


**Example:  Lists available roles to manage service access: JSON response**


.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   Content-Length: 3872
   Connection: keep-alive
   Link: <http://identity.api.rackspacecloud.com/cloud/v2.0/OS-KSADM/roles?marker=75&limit=25>; rel="last",
     <http://identity.api.rackspacecloud.com/cloud/v2.0/OS-KSADM/roles?marker=25&limit=25>; rel="next"


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
