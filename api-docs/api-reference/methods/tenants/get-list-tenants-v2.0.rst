.. _get-list-tenants-v2.0:

List tenants
~~~~~~~~~~~~

.. code::

    GET /v2.0/tenants

Get a list of tenants, or look up a tenant by name.

Identity administrators can use this operation to retrieve a list of tenants
or an individual tenant by name.



This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |The request completed    |
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

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|name                      |String *(Required)*      |The name of the tenant.  |
+--------------------------+-------------------------+-------------------------+
|X-Auth-Token              |String *(Required)*      |A valid authentication   |
|                          |                         |token issued to a user   |
|                          |                         |with administrative      |
|                          |                         |privileges.              |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.




Response
--------

This table shows the body parameters for the response:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|tenants                   |String                   |The tenants object       |
|                          |                         |returns the collection of|
|                          |                         |tenant resources that    |
|                          |                         |the authenticated user   |
|                          |                         |has permission to view.  |
+--------------------------+-------------------------+-------------------------+
|tenants.\                 |                         |The tenant object        |
|**tenant**                |                         |returns the following    |
|                          |                         |tenant account           |
|                          |                         |information: name,       |
|                          |                         |tenant id, account       |
|                          |                         |status, and description. |
+--------------------------+-------------------------+-------------------------+
|tenant.\                  |String *(Required)*      |The unique,              |
|**id**                    |                         |system-generated ID      |
|                          |                         |that identifies the      |
|                          |                         |in the Rackspace system. |
+--------------------------+-------------------------+-------------------------+
|tenant.\                  |Boolean                  |Indicates whether the    |
|**enabled**               |                         |tenant is currently      |
|                          |                         |active for use with the  |
|                          |                         |Rackspace Cloud.         |
+--------------------------+-------------------------+-------------------------+
|tenant\                   |String                   |The name to display      |
|**display-name**          |                         |in user interfaces       |
|                          |                         |if it has been specified.|
+--------------------------+-------------------------+-------------------------+
|tenant.\                  |String                   |Describes the tenant     |
|**description**           |                         |tenant account i         |
|                          |                         |if specified.            |
+--------------------------+-------------------------+-------------------------+
|tenant.\                  |String                   |The answer that the user |
|**name**                  |                         |can provide to verify an |
|                          |                         |account.                 |
+--------------------------+-------------------------+-------------------------+


**Example:  List tenants response XML**

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/xml; charset=UTF-8
   Content-Length: 200
   Date: Sun, 1 Jan 2011 9:00:00 GMT

   <?xml version="1.0" encoding="UTF-8"?>
   <tenants
      xmlns="http://docs.openstack.org/identity/api/v2.0"
      xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
      xmlns:atom="http://www.w3.org/2005/Atom">
      <tenant display-name="Star Wars" enabled="true" id="5781234" name="star_wars">
        <description>Used to manage the Star Wars games</description>
      </tenant>
      <tenant display-name="Star Wars" enabled="true" id="5781234_FS" name="start_wars_pictures">
        <description>Used to manage the pictures for Star Wars</description>
      </tenant>
    </tenants>


**Example:  List tenants response JSON**

.. code::

   {
     "tenants": [
       {
         "id": "5784574",
         "enabled": true,
         "display-name": "Star Wars",
         "description": "Used to manage the Star Wars games",
         "name": "star_wars"
        },
       {
         "id": ""5781234_FS",
         "enabled": true,
         "display-name": "Star Wars",
         "description": "Used to manage the pictures for Start Wars",
         "name": "start_wars_pictures"
       }
      ]
     }
