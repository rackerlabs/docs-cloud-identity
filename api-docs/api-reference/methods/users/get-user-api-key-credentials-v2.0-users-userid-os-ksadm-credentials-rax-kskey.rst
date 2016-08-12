.. _get-get-user-api-key-credentials-v2.0:

Get user credentials
~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /v2.0/users/{userId}/OS-KSADM/credentials/RAX-KSKEY:apiKeyCredentials

Use this operation to list API key credentials for a specified user, include the
user ID in the request. If you don't know the ID, use the use
:ref:`List users <get-list-users-v2.0>` operation to find it.



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




**Example: List API key credentials: XML request header**


.. code::

   GET /users/00001e59ccb741dfafbba59b58123456/OS-KSADM/credentials/RAX-KSKEY:apiKeyCredentials HTTP/1.1
   Host: v2.0
   Accept: application/xml
   Content-type: application/xml
   X-Auth-Token: AAA3IQ7zIvKbovOwFOyz4tZfOXy3O34UI12XUg8nusYS...





**Example: List API key credentials: JSON request header**


.. code::

   GET /users/00001e59ccb741dfafbba59b58123456/OS-KSADM/credentials HTTP/1.1
   Host: v2.0
   Accept: application/json
   Content-type: application/json
   X-Auth-Token: AAA3IQ7zIvKbovOwFOyz4tZfOXy3O34UI12XUg8nusYS...





Response
--------

**Example: Get user API key credentials: XML response**


.. code::

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <apiKeyCredentials
   	xmlns="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"
   	xmlns:ns2="http://www.w3.org/2005/Atom"
   	xmlns:ns3="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
   	xmlns:ns4="http://docs.openstack.org/identity/api/v2.0"
   	xmlns:ns5="http://docs.rackspace.com/identity/api/ext/RAX-KSGRP/v1.0"
   	xmlns:ns6="http://docs.rackspace.com/identity/api/ext/RAX-KSQA/v1.0"
   	xmlns:ns7="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
   	xmlns:ns8="http://docs.openstack.org/identity/api/ext/OS-KSEC2/v1.0" username="1406847123456" apiKey="cffeab0e6d0d472f84b5c20c70123456"/>





**Example: Get user API key credentials: JSON response**


.. code::

   {
       "RAX-KSKEY:apiKeyCredentials": {
           "username": "1406847123456",
           "apiKey": "cffeab0e6d0d472f84b5c20c70123456"
       }
   }
