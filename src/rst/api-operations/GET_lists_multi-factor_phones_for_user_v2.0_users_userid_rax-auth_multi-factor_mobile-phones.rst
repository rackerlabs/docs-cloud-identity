=============================================================================
Lists Multi-Factor Phones For User -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Lists Multi-Factor Phones For User
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_lists_multi-factor_phones_for_user_v2.0_users_userid_rax-auth_multi-factor_mobile-phones.rst#request>`__
`Response <GET_lists_multi-factor_phones_for_user_v2.0_users_userid_rax-auth_multi-factor_mobile-phones.rst#response>`__

.. code-block:: javascript

    GET /v2.0/users/{userId}/RAX-AUTH/multi-factor/mobile-phones

Lists the mobile phones associated with the specified user account.

A user or Identity administrator impersonating a user can use this operation to list the mobile phones associated with a user account.

You can retrieve a specific phone by including the unique, system-generated ID assigned to the phone when it was added to the Rackspace Cloud account.

An account can have up to one mobile phone configured for multi-factor authentication.

If you don't know the user ID, use the List user operation to find it.



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
|{userId}                  |string *(Required)*      |The unique, system-      |
|                          |                         |generated user ID for an |
|                          |                         |account.                 |
+--------------------------+-------------------------+-------------------------+
|X-Auth-Token              |string *(Required)*      |A valid authentication   |
|                          |                         |token.                   |
+--------------------------+-------------------------+-------------------------+








**Example List multi-factor phones for user: XML request**


.. code::

    GET /v2.0/users/e0fb2b4ddb594819b697d0048614c12345/RAX-AUTH/multi-factor/mobile-phones HTTP/1.1
    Host: identity.api.rackspacecloud.com
    Accept: application/json
    X-Auth-Token: 9b830c07c29f4d17a7e53d2341301234
    Content-type: application/json


**Example List multi-factor phones for user request: JSON request**


.. code::

    GET /v2.0/users/e0fb2b4ddb594819b697d0048614c12345/RAX-AUTH/multi-factor/mobile-phones HTTP/1.1
    Host: identity.api.rackspacecloud.com
    Accept: application/json
    X-Auth-Token: 9b830c07c29f4d17a7e53d2341301234
    Content-type: application/json


Response
^^^^^^^^^^^^^^^^^^


This table shows the body parameters for the response:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|RAX-AUTH:mobilePhones     |object *(Required)*      |An array that returns    |
|                          |                         |phone ID and status      |
|                          |                         |information.             |
+--------------------------+-------------------------+-------------------------+
|id                        |string *(Required)*      |A unique, system-        |
|                          |                         |generated string that    |
|                          |                         |identifies the mobile    |
|                          |                         |phone in the Identity    |
|                          |                         |service.                 |
+--------------------------+-------------------------+-------------------------+
|number                    |string *(Required)*      |Phone number of the      |
|                          |                         |device associated with   |
|                          |                         |the user account. Use    |
|                          |                         |the Add mobile phone     |
|                          |                         |operation to add a phone |
|                          |                         |to the account. Use the  |
|                          |                         |remove multi-factor      |
|                          |                         |operation to delete      |
|                          |                         |phones from the account. |
+--------------------------+-------------------------+-------------------------+
|verified                  |Boolean *(Required)*     |A Boolean value that     |
|                          |                         |indicates whether the    |
|                          |                         |phone can be used to     |
|                          |                         |authenticate to the      |
|                          |                         |Identity service. Phones |
|                          |                         |can be verified by using |
|                          |                         |the Send verification    |
|                          |                         |code and Verify device   |
|                          |                         |operations.              |
+--------------------------+-------------------------+-------------------------+





**Example Lists Multi-Factor Phones For User: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <mobilePhones
         xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
         xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
         xmlns:atom="http://www.w3.org/2005/Atom" xmlns:identity="http://docs.openstack.org/identity/api/v2.0">
         <mobilePhone id="12345" number="+1 265-894-3489" verified="true"/>
    </mobilePhones>
    


**Example Lists Multi-Factor Phones For User: JSON request**


.. code::

    {
      "RAX-AUTH:mobilePhones": [
        {
          "id": "12345",
          "verified": true,
          "number": "12658943489"
        }
      ]
    }

