.. _get-list-credentials-v2.0-users-userid-os-ksadm-credentials:

List credentials
~~~~~~~~~~~~~~~~

.. code::

    GET /v2.0/users/{userId}/OS-KSADM/credentials

List available credentials for the specified user.

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
|X-Auth-Token              |String *(Required)*      |A valid admin            |
|                          |                         |authentication token.    |
+--------------------------+-------------------------+-------------------------+
|{userId}                  |String *(Required)*      |A user ID assigned by    |
|                          |                         |system when user is      |
|                          |                         |added.                   |
+--------------------------+-------------------------+-------------------------+


This operation does not accept a request body.

**Example: List credentials: XML request header**


.. code::

   GET /users/00001e59ccb741dfafbba59b58123456/OS-KSADM/credentials HTTP/1.1
   Host: v2.0
   Accept: application/xml
   Content-type: application/xml
   X-Auth-Token: AAA3IQ7zIvKbovOwFOyz4tZfOXy3O34UI12XUg8nusYS...


**Example: List credentials: JSON request header**


.. code::

   GET /users/00001e59ccb741dfafbba59b58123456/OS-KSADM/credentials HTTP/1.1
   Host: v2.0
   Accept: application/json
   Content-type: application/json
   X-Auth-Token: AAA3IQ7zIvKbovOwFOyz4tZfOXy3O34UI12XUg8nusYS...


Response
--------

**Example: List credentials: JSON response**


.. code::

   {
       "credentials": [
           {
               "RAX-KSKEY:apiKeyCredentials": {
                   "username": "1406847123456",
                   "apiKey": "cffeab0e6d0d472f84b5c20c70123456"
               }
           }
       ]
   }



**Example: List credentials: XML response**


.. code::

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <credentials
     xmlns="http://docs.openstack.org/identity/api/v2.0"
     xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
     xmlns:rax-kskey="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"
     xmlns:os-ksec2="http://docs.openstack.org/identity/api/ext/OS-KSEC2/v1.0"
     xmlns:rax-ksqa="http://docs.rackspace.com/identity/api/ext/RAX-KSQA/v1.0"
     xmlns:atom="http://www.w3.org/2005/Atom"
     xmlns:ns7="http://docs.rackspace.com/identity/api/ext/RAX-KSGRP/v1.0"
     xmlns:os-ksadm="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0">
     <rax-kskey:apiKeyCredentials username="1406847123456" apiKey="cffeab0e6d0d472f84b5c20c70123456"/>
   </credentials>
