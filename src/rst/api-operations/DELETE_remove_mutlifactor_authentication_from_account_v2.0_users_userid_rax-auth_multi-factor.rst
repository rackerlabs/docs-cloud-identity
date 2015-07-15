=============================================================================
Remove Mutlifactor Authentication From Account -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Remove Mutlifactor Authentication From Account
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <DELETE_remove_mutlifactor_authentication_from_account_v2.0_users_userid_rax-auth_multi-factor.rst#request>`__
`Response <DELETE_remove_mutlifactor_authentication_from_account_v2.0_users_userid_rax-auth_multi-factor.rst#response>`__

.. code-block:: javascript

    DELETE /v2.0/users/{userId}/RAX-AUTH/multi-factor

Removes the multi-factor authentication setting and all associated mobile phones from your user account.

This operation removes the multi-factor authentication setting from your account along with all phones associated with the account. To disable the feature without removing phones, use the update multi-factor settings on account operation to disable multi-factor authentication on the account.

This operation can be completed only on the user account used to submit the request. Attempts to run it for a different user ID result in a 403 error message.



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
|{userId}                  |string                   |The unique, system-      |
|                          |                         |generated user ID for an |
|                          |                         |account.                 |
+--------------------------+-------------------------+-------------------------+
|X-Auth-Token              |string *(Required)*      |A valid authentication   |
|                          |                         |token.                   |
+--------------------------+-------------------------+-------------------------+








**Example Remove multi-factor authentication: XML request**


.. code::

    DELETE /v2.0/users/e0fb2b4ddb594819b697d0048614c117/RAX-AUTH/multi-factor HTTP/1.1
    Host: identity.api.rackspacecloud.com
    Accept: application/xml
    X-Auth-Token: ab502872c7cc415483c945bcfc77322c
    Content-type: application/xml


**Example Remove multi-factor authentication: JSON request**


.. code::

    DELETE /v2.0/users/e0fb2b4ddb594819b697d0048614c117/RAX-AUTH/multi-factor HTTP/1.1
    Host: identity.api.rackspacecloud.com
    Accept: application/json
    X-Auth-Token: ab502872c7cc415483c945bcfc77322c
    Content-type: application/json


Response
^^^^^^^^^^^^^^^^^^




