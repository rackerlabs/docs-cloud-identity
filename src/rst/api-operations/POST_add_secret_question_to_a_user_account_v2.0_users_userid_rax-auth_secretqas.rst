=============================================================================
Add Secret Question To A User Account -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Add Secret Question To A User Account
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <POST_add_secret_question_to_a_user_account_v2.0_users_userid_rax-auth_secretqas.rst#request>`__
`Response <POST_add_secret_question_to_a_user_account_v2.0_users_userid_rax-auth_secretqas.rst#response>`__

.. code-block:: javascript

    POST /v2.0/users/{userId}/RAX-AUTH/secretqas

Adds a secret question and answer to a user account.

The Identity service provides a list of security questions that can be used to verify account access. Administrators and users can add one of these questions to a user account with a unique answer that can be used to confirm identity before granting access to the account or account information. Users can only add a security question to their own account.

If the account already has a secret question and answer, this operation replaces the existing information with the values specified in the request body.

Use the Get questions API operation to list the available questions and associated IDs.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |The request succeeded.   |
+--------------------------+-------------------------+-------------------------+
|409                       |Conflict                 |The request could not be |
|                          |                         |completed due to a       |
|                          |                         |conflict with the        |
|                          |                         |current state of the     |
|                          |                         |resource.                |
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





This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|id                        |string *(Required)*      |The ID of the secret     |
|                          |                         |question to add to the   |
|                          |                         |account.                 |
+--------------------------+-------------------------+-------------------------+
|answer                    |string *(Required)*      |The answer that the user |
|                          |                         |can provide to verify an |
|                          |                         |account.                 |
+--------------------------+-------------------------+-------------------------+





**Example Add Secret Question To A User Account: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <secretqa answer="Himalayas" id="1"
        xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
        xmlns:atom="http://www.w3.org/2005/Atom" 
        xmlns:identity="http://docs.openstack.org/identity/api/v2.0"/>


**Example Add Secret Question To A User Account: JSON request**


.. code::

    {
       "RAX-AUTH:secretqa": 
         {
           "id": "1",
           "answer": "Himalayas",
         }
    }


Response
^^^^^^^^^^^^^^^^^^





**Example Add Secret Question To A User Account: JSON request**


.. code::

    POST /v2.0/users/266d3c8982534378bf88f64db2c916da/RAX-AUTH/secretqas HTTP/1.1
    Host: staging.identity-internal.api.rackspacecloud.com
    X-Auth-Token: 0f6e9f63600142f0a970911583522217
    

