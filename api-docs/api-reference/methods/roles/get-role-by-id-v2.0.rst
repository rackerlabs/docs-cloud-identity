.. _get-role-by-id-v2.0:

Get role by ID
~~~~~~~~~~~~~~~

.. code::

    GET /v2.0/OS-KSADM/roles/{roleId}

This operation retrieves information about the specified role ID.


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
-------

This table shows the header and URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|X-Auth-Token              |Header                   |A valid admin            |
|                          |String *(Required)*      |authentication token.    |
+--------------------------+-------------------------+-------------------------+
|{userId}                  |URI                      |A user ID assigned by    |
|                          |String *(Required)*      |system when user is      |
|                          |                         |added.                   |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.


**Example:  Get role by ID request: XML**


.. code::

   GET /v2.0/OS-KSADM/roles/10000209 HTTP/1.1
   Host: identity.api.rackspacecloud.com
   X-Auth-Token:82994d2fb9a0483a85b6ba622c2c4934
   Accept: application/xml
   Content-type: application/xml


**Example:  Get role by ID request: JSON**


.. code::

   GET /v2.0/OS-KSADM/roles/10000209 HTTP/1.1
   Host: identity.api.rackspacecloud.com
   X-Auth-Token:82994d2fb9a0483a85b6ba622c2c4934
   Accept: application/json
   Content-type: application/json



Response
--------

This table shows the body parameters for the response:

+---------------------------+-------------------------+-------------------------+
|Name                       |Type                     |Description              |
+===========================+=========================+=========================+
|role                       |Object                   |Returns the information  |
|                           |                         |role information for the |
|                           |                         |specified role ID.       |
+---------------------------+-------------------------+-------------------------+
|role.**id**                |Int                      |The role ID.             |
+---------------------------+-------------------------+-------------------------+
|role.**name**              |String                   |The role name.           |
+---------------------------+-------------------------+-------------------------+
|role.**description**       |String                   |The role description.    |
+---------------------------+-------------------------+-------------------------+
|role.**serviceId**         |String                   |The id for the Rackspace |
|                           |                         |Cloud service to which   |
|                           |                         |the role applies.        |
+---------------------------+-------------------------+-------------------------+
|role.**RAX-AUTH:propagate**|Boolean *(Optional)*     |Indicates whether this   |
|                           |                         |role is assigned to an   |
|                           |                         |account owner            |
|                           |                         |(identity:user-admin)    |
|                           |                         |and automatically        |
|                           |                         |inherited by all account |
|                           |                         |users (identity:default).|
+---------------------------+-------------------------+-------------------------+


**Example:  Get role by ID response: XML**


.. code::

   HTTP/1.1 200 OK
   Content-Type: application/xml



.. code::

   <?xml version="1.0" encoding="UTF-8"?>

   <role xmlns="http://docs.openstack.org/identity/api/v2.0"
     id="123" name="database:admin" description="Admin role for database service" \
     serviceId="abc4321ebabeeabb70a0e702a4626977c331d5c4" rax-auth:propagate="false"/>




**Example:  Get role by ID response: JSON**


.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json



.. code::

   {
     "role": {
       "id": "123",
       "serviceId": "abc4321ebabeeabb70a0e702a4626977c331d5c4"
       "description": "Admin role for database service",
       "name": "database:admin",
       "RAX-AUTH:propagate": false
     }
   }
