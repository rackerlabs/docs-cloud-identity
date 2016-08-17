.. _get-multifactor-phones-by-deviceid-v2.0:

Retrieve multi-factor mobile phone associated to a user by device ID
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET v2.0/users/{userId}/RAX-AUTH/multi-factor/mobile-phones/{mobilePhoneId}

Use this operation to retrieve the multi-factor mobile phone for a specified
user account by  device ID.  This request is useful if you want to locate the
phone number for a device  registered to a user account for multi-factor
authentication.


This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|204                       |No content               |The request succeeded.   |
|                          |                         |The server fulfilled the |
|                          |                         |request but does not     |
|                          |                         |need to return a body.   |
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
|{userId}                  |URI                      |The unique, system-      |
|                          |String *(Required)*      |generated user ID for an |
|                          |                         |account.                 |
+--------------------------+-------------------------+-------------------------+
|{mobilePhoneId}           |URI                      |The unique, system-      |
|                          |String *(Required)*      |generated ID for a       |
|                          |                         |mobile phone that has    |
|                          |                         |been registered for use  |
|                          |                         |as a multi-factor        |
|                          |                         |authentication device.   |
+--------------------------+-------------------------+-------------------------+


This operation does not accept a request body.


**Example: Retrieve multi-factor phone for a user HTTP request header: XML**

.. code::

   GET /v2.0/users/e0fb2b4ddb594819b697d0048614c12345/RAX-AUTH/multi-factor/mobile-phones HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/json
   X-Auth-Token: 9b830c07c29f4d17a7e53d2341301234
   Content-type: application/json


**Example: Retrieve multi-factor phone for user by device ID request header: JSON**


.. code::

   GET /v2.0/users/e0fb2b4ddb594819b697d0048614c12345/RAX-AUTH/multi-factor/mobile-phones HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/json
   X-Auth-Token: 9b830c07c29f4d17a7e53d2341301234
   Content-type: application/json


Response
--------

This table shows the body parameters for the response:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|RAX-AUTH:mobilePhones     |Object *(Required)*      |An array that returns    |
|                          |                         |phone ID and status      |
|                          |                         |information.             |
+--------------------------+-------------------------+-------------------------+
|RAX-AUTH:mobilePhones.\   |String *(Required)*      |A unique, system-        |
|**id**                    |                         |generated string that    |
|                          |                         |identifies the mobile    |
|                          |                         |phone in the Identity    |
|                          |                         |service.                 |
+--------------------------+-------------------------+-------------------------+
|RAX-AUTH:mobilePhones.\   |String *(Required)*      |Phone number of the      |
|**number**                |                         |device associated with   |
|                          |                         |the user account. Use    |
|                          |                         |the Add mobile phone     |
|                          |                         |operation to add a phone |
|                          |                         |to the account. Use the  |
|                          |                         |remove multi-factor      |
|                          |                         |operation to delete      |
|                          |                         |phones from the account. |
+--------------------------+-------------------------+-------------------------+
|RAX-AUTH:mobilePhones.\   |Boolean *(Optional)*     |A Boolean value that     |
|verified                  |                         |indicates whether the    |
|                          |                         |phone can be used to     |
|                          |                         |authenticate to the      |
|                          |                         |Identity service. Phones |
|                          |                         |can be verified by using |
|                          |                         |the Send verification    |
|                          |                         |code and Verify device   |
|                          |                         |operations.              |
+--------------------------+-------------------------+-------------------------+



**Example: Lists multi-factor phones for user response: XML**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <mobilePhone id="12345" number="12658943489" verified="false"
     xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
     xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
     xmlns:atom="http://www.w3.org/2005/Atom" xmlns:identity="http://docs.openstack.org/identity/api/v2.0"/>



**Example: Lists multi-factor phones for user response: JSON**


.. code::

   {
  	"RAX-AUTH:mobilePhone": {
    	"id": "12345",
    	"verified": false,
    	"number": "12658943489"
     }
   }
