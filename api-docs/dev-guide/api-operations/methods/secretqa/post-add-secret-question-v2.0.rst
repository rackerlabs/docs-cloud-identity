.. _post-create-a-secret-question-v2.0:

Add a secret question
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /v2.0/users/{userId}/RAX-AUTH/secretqas

Creates a secret question that can be added to user accounts.

The Identity service provides a list of security questions that can be used to verify 
account access. Administrators and users can add one of these questions to a user account 
with a unique answer that can be used to confirm identity before granting access to the 
account or account information. Users can only add a security question to their own account.

If the account already has a secret question and answer, this operation replaces the 
existing information with the values specified in the request body.


This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |                         |The request succeeded.   |
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
|409                       |Conflict                 |The request could not be |
|                          |                         |completed due to a       |
|                          |                         |conflict with the        |
|                          |                         |current state of the     |
|                          |                         |resource.                |
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
""""""""""""""""

This table shows the header parameter for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|X-Auth-Token              |Header                   |A valid                  |
|                          |String *(Required)*      |authentication token.    |
+--------------------------+-------------------------+-------------------------+
|{userId}                  |URI                      |A user ID assigned by    |
|                          |String *(Required)*      |system when user is      |
|                          |                         |added.                   |
+--------------------------+-------------------------+-------------------------+


This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|id                        |String *(Required)*      |The ID of the secret     |
|                          |                         |question to add to the   |
|                          |                         |account.                 |
+--------------------------+-------------------------+-------------------------+
|answer                    |String *(Required)*      |The answer that the user |
|                          |                         |can provide to verify an |
|                          |                         |account.                 |
+--------------------------+-------------------------+-------------------------+

**Example:  Create a secret question request: XML**

.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <secretqa answer="Himalayas" id="1"
    xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
    xmlns:atom="http://www.w3.org/2005/Atom"
    xmlns:identity="http://docs.openstack.org/identity/api/v2.0"/>
   

**Example:  Create a secret question request: JSON**

.. code::

   {
   "RAX-AUTH:secretqa": 
     {
       "id": "1",
       "answer": "Himalayas",
     }
   }


Response
""""""""""""""""

This table shows the header parameters for the response:

**Example:  Create a secret question HTTP response header**

.. code:

	POST /v2.0/users/266d3c8982534378bf88f64db2c916da/RAX-AUTH/secretqas HTTP/1.1
	Host: staging.identity-internal.api.rackspacecloud.com
	X-Auth-Token: 0f6e9f63600142f0a970911583522217




