.. _post-verifies-a-mobile-phone-v2.0:

Verify a mobile phone
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /v2.0/users/{userId}/RAX-AUTH/multi-factor/mobile-phones/{phoneId}/verify

Use this operation to submit the verification PIN from the SMS text message
sent by  Rackspace. After the PIN is accepted, use the Update settings for
mulit-factor  authentication operation to enable multi-factor authentication on
the user account.

When you send the verification code, include the ``phoneId`` in the API
request.  If you don't know the ID, use the :ref:`List phones for user
<get-multifactor-phones-for-user-v2.0>` operation to get it.

This operation can only be completed from the user account that the phone is
associated with. The operation fails if the PIN is expired, or if it doesn't
match the code issued by the Rackspace verification service.

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
|{userId}                  |URI                      |The unique, system-      |
|                          |String *(Required)*      |generated user ID for an |
|                          |                         |account.                 |
+--------------------------+-------------------------+-------------------------+
|{phoneid}                 |String *(Required)*      |The unique, system-      |
|                          |                         |generated ID assigned    |
|                          |                         |when a phone is added to |
|                          |                         |an account.              |
+--------------------------+-------------------------+-------------------------+


This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|code                      |String *(Required)*      |The unique PIN code from |
|                          |                         |the SMS text message     |
|                          |                         |sent by the Rackspace    |
|                          |                         |Cloud verification       |
|                          |                         |service.                 |
+--------------------------+-------------------------+-------------------------+





**Example: Verify device: XML request**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <verificationCode
        code="1234"
        xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
        xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
        xmlns:atom="http://www.w3.org/2005/Atom"
        xmlns:identity="http://docs.openstack.org/identity/api/v2.0"/>

**Example: Verify device: JSON request**


.. code::

   {
       "RAX-AUTH:verificationCode": {
           "code": "1234"
       }
   }





Response
--------

This operation does not return a response body.
