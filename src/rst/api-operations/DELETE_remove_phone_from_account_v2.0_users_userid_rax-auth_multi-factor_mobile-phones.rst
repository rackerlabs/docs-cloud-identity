=============================================================================
Remove Phone From Account -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Remove Phone From Account
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <DELETE_remove_phone_from_account_v2.0_users_userid_rax-auth_multi-factor_mobile-phones.rst#request>`__
`Response <DELETE_remove_phone_from_account_v2.0_users_userid_rax-auth_multi-factor_mobile-phones.rst#response>`__

.. code-block:: javascript

    DELETE /v2.0/users/{userId}/RAX-AUTH/multi-factor/mobile-phones

Removes a phone number associated with a user account to support multi-factor authentication.

This operation removes the multi-factor authentication setting from your account along with all phones associated with the account. To disable the feature without removing phones, use the Disable multi-factor setting operation.

This operation allows users and administrators to remove a mobile phone number added to an account to support multi-factor authentication. You can remove the number if multi-factor authentication is disabled, or if the user has decided to use an OTP device for multi-factor authentication.

This operation can only be completed from the user account submitting the request. Attempts to run it for a different user ID result in a 403 error message.



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








**Example Remove Phone From Account: XML request**


.. code::

    DELETE /v2.0/users/e0fb2b4ddb594819b697d0048614c117/RAX-AUTH/multi-factor/1234 HTTP/1.1
    Host: identity.api.rackspacecloud.com
    Accept: application/xml
    X-Auth-Token: 9b830c07c29f4d17a7e53d2341301234
    Content-type: application/xml


**Example Remove Phone From Account: JSON request**


.. code::

    DELETE /v2.0/users/e0fb2b4ddb594819b697d0048614c117/RAX-AUTH/multi-factor/1234 HTTP/1.1
    Host: identity.api.rackspacecloud.com
    Accept: application/json
    X-Auth-Token: 9b830c07c29f4d17a7e53d2341301234
    Content-type: application/json


Response
^^^^^^^^^^^^^^^^^^




