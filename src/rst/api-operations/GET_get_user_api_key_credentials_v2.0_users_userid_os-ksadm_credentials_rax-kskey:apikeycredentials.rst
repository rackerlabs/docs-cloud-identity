=============================================================================
Get User Api Key Credentials -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Get User Api Key Credentials
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_get_user_api_key_credentials_v2.0_users_userid_os-ksadm_credentials_rax-kskey:apikeycredentials.rst#request>`__
`Response <GET_get_user_api_key_credentials_v2.0_users_userid_os-ksadm_credentials_rax-kskey:apikeycredentials.rst#response>`__

.. code-block:: javascript

    GET /v2.0/users/{userId}/OS-KSADM/credentials/RAX-KSKEY:apiKeyCredentials

Get user credentials.

To list API key credentials for a specified user, include the user ID in the request. If you don't know the ID, use the `List users <GET_admin-listUsers_v2.0_users_User_Calls.html>`__ operation to find it.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |The request completed    |
|                          |                         |successfully.            |
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
|X-Auth-Token              |xsd:string *(Required)*  |A valid admin            |
|                          |                         |authentication token.    |
+--------------------------+-------------------------+-------------------------+
|{userId}                  |xsd:string *(Required)*  |A user ID assigned by    |
|                          |                         |system when user is      |
|                          |                         |added.                   |
+--------------------------+-------------------------+-------------------------+








Response
^^^^^^^^^^^^^^^^^^





**Example Get User Api Key Credentials: JSON request**


.. code::

    {
        "RAX-KSKEY:apiKeyCredentials":{
            "username":"demoauthor",
            "apiKey":"aaaaa-bbbbb-ccccc-12345678"
        }
    }


**Example Get User Api Key Credentials: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <apiKeyCredentials
    	xmlns="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"
    	username="demoauthor"
    	apiKey="aaaaa-bbbbb-ccccc-12345678"/>

