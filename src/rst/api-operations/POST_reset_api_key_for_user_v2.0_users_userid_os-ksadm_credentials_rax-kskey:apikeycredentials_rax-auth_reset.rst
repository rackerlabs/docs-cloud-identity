=============================================================================
Reset Api Key For User -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Reset Api Key For User
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <POST_reset_api_key_for_user_v2.0_users_userid_os-ksadm_credentials_rax-kskey:apikeycredentials_rax-auth_reset.rst#request>`__
`Response <POST_reset_api_key_for_user_v2.0_users_userid_os-ksadm_credentials_rax-kskey:apikeycredentials_rax-auth_reset.rst#response>`__

.. code-block:: javascript

    POST /v2.0/users/{userId}/OS-KSADM/credentials/RAX-KSKEY:apiKeyCredentials/RAX-AUTH/reset

Resets the API Key for a specified user account.

para>We recommend that you routinely reset passwords and API keys. This API key reset operation returns the new API key for the user account. Unlike updating the password, the API key reset does not revoke existing tokens. Administrators can use the Revoke Token operation to invalidate the token for a user.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |The request succeeded.   |
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
|415                       |Bad Media Type           |Bad media type. This may |
|                          |                         |result if the wrong      |
|                          |                         |media type is used in    |
|                          |                         |the API request. Check   |
|                          |                         |the content-type and     |
|                          |                         |accept headers included  |
|                          |                         |in the request.          |
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
|                          |                         |token                    |
+--------------------------+-------------------------+-------------------------+








Response
^^^^^^^^^^^^^^^^^^





**Example Reset Api Key For User: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <apiKeyCredentials apiKey="aaaaa-bbbbb-ccccc-12345678"
         username="jqsmith"
         xmlns="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"
         xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
         xmlns:atom="http://www.w3.org/2005/Atom" 
         xmlns:identity="http://docs.openstack.org/identity/api/v2.0"/>


**Example Reset Api Key For User: JSON request**


.. code::

    {
      "RAX-KSKEY:apiKeyCredentials": {
        "username": "jqsmith",
        "apiKey": "aaaaa-bbbbb-ccccc-12345678"
      }
    }

