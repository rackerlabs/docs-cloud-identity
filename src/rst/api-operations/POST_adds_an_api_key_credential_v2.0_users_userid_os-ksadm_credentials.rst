=============================================================================
Adds An Api Key Credential -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Adds An Api Key Credential
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <POST_adds_an_api_key_credential_v2.0_users_userid_os-ksadm_credentials.rst#request>`__
`Response <POST_adds_an_api_key_credential_v2.0_users_userid_os-ksadm_credentials.rst#response>`__

.. code-block:: javascript

    POST /v2.0/users/{userId}/OS-KSADM/credentials

Adds an API credential to a specified user account.

Identity administrators can update a user account to add an API credential.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|201                       |Created                  |The request completed    |
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
|415                       |Bad Media Type           |Bad media type. This may |
|                          |                         |result if the wrong      |
|                          |                         |media type is used in    |
|                          |                         |the API request. Check   |
|                          |                         |the content-type and     |
|                          |                         |accept headers included  |
|                          |                         |in the request.          |
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








**Example Adds An Api Key Credential: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <apiKeyCredentials
    	xmlns="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"
    	username="demoauthor"
    	apiKey="aaaaa-bbbbb-ccccc-12345678"/>


**Example Adds An Api Key Credential: JSON request**


.. code::

    {
        "RAX-KSKEY:apiKeyCredentials":{
            "username":"demoauthor",
            "apiKey":"aaaaa-bbbbb-ccccc-12345678"
        }
    }


Response
^^^^^^^^^^^^^^^^^^





**Example Adds An Api Key Credential: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <apiKeyCredentials
    	xmlns="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"
    	username="demoauthor"
    	apiKey="aaaaa-bbbbb-ccccc-12345678"/>


**Example Adds An Api Key Credential: JSON request**


.. code::

    {
        "RAX-KSKEY:apiKeyCredentials":{
            "username":"demoauthor",
            "apiKey":"aaaaa-bbbbb-ccccc-12345678"
        }
    }

