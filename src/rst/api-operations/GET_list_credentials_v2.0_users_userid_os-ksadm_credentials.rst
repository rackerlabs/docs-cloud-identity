=============================================================================
List Credentials -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

List Credentials
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_list_credentials_v2.0_users_userid_os-ksadm_credentials.rst#request>`__
`Response <GET_list_credentials_v2.0_users_userid_os-ksadm_credentials.rst#response>`__

.. code-block:: javascript

    GET /v2.0/users/{userId}/OS-KSADM/credentials

List credentials.

List credentials.



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





**Example List Credentials: JSON request**


.. code::

    {
        "credentials":[{
                "passwordCredentials":{
                    "username":"test_user",
                    "password":"mypass"
                }
            },
            {
                "RAX-KSKEY:apiKeyCredentials":{
                    "username":"test_user",
                    "apiKey":"aaaaa-bbbbb-ccccc-12345678"
                }
            }
        ],
        "credentials_links":[]
    }
    


**Example List Credentials: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <credentials xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xmlns="http://docs.openstack.org/identity/api/v2.0">
        <passwordCredentials username="test_user" password="test"/>
        <apiKeyCredentials
    	xmlns="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"
    	username="testuser"
    	apiKey="aaaaa-bbbbb-ccccc-12345678"/>
    </credentials>
    

