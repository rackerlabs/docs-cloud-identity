
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _post-sends-a-verfication-code-to-a-phone-v2.0-users-userid-rax-auth-multi-factor-mobile-phones-phoneid-verificationcode:

Sends a verfication code to a phone
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /v2.0/users/{userId}/RAX-AUTH/multi-factor/mobile-phones/{phoneId}/verificationcode

Sends an SMS message with a PIN code to a phone added to an account for multi-factor authentication.

After you update an account with a mobile phone number for multi-factor authentication, Rackspace must confirm that the user has the phone before it can be enabled for use in the authentication process.

When you send the verification code, include the ``phoneId`` in the API request. If you don't know the ID, use the `List multi-factor devices associated with <GET_getMobilePhonesForUser_v2.0_users__userId__RAX-AUTH_multi-factor_mobile-phones_Multifactor_Calls.html>`__ operation to get it.

When you send the verification code, include the ``phoneId`` in the API request. If you don't know the ID, use the `List multi-factor devices for user <GET_getMobilePhonesForUser_v2.0_users__userId__RAX-AUTH_multi-factor_mobile-phones_Multifactor_Calls_client.html>`__ operation to get it.

After you submit request, the Rackspace verification service sends a PIN to the specified phone via SMS text message. Each PIN has a system-defined expiration time determined by the Identity service system configuration. After receiving the PIN, use the Verify a mobile phone operation to submit the PIN to the Identity service to confirm the device for use with multi-factor authentication services. 

.. important::
   In the Send Verify request, the ``X-Auth-Token`` header parameter value must specify a valid authentication token ID for the user account associated with the mobile phone. If you submit an authentication token from any other account, the operation fails.
   
   



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|202                       |Accepted                 |The request was accepted |
|                          |                         |for processing.          |
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
""""""""""""""""




This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{userId}                  |String *(Required)*      |The unique, system-      |
|                          |                         |generated user ID for an |
|                          |                         |account.                 |
+--------------------------+-------------------------+-------------------------+
|X-Auth-Token              |String *(Required)*      |A valid authentication   |
|                          |                         |token.                   |
+--------------------------+-------------------------+-------------------------+
|{phoneId}                 |String *(Required)*      |The ID for the phone     |
|                          |                         |associated with the user |
|                          |                         |account.                 |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




**Example Send verification code: JSON request in a cURL command**


 ``$ curl $AUTH_URL/v2.0/users/$USER_ID/RAX-AUTH/multi-factor/mobile-phones/$PHONE_ID/verificationcode \        -X POST \        -H "Content-Type: application/json" \        -H "Accept: application/json" \        -H "X-Auth-Token: $AUTH_TOKEN"        | python -m json.tool`` .. note::
   This example assumes that the endpoint URL, user ID, and your authentication token have been exported to environment variables.
   
   




Response
""""""""""""""""






This operation does not return a response body.




