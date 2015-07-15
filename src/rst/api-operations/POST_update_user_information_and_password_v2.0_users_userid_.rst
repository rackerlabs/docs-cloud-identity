=============================================================================
Update User Information And Password -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Update User Information And Password
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <POST_update_user_information_and_password_v2.0_users_userid_.rst#request>`__
`Response <POST_update_user_information_and_password_v2.0_users_userid_.rst#response>`__

.. code-block:: javascript

    POST /v2.0/users/{userId}

Update user information and password.

The Update user operation acts upon the user specified by ``userId``. Before you update a user account, use the `Get user by id <GET_admin-getUserById_v2.0_users__userId__User_Calls.html>`__ operation to verify that the user name, email account, and status associated with ``userId`` match the account you want to update.

Only include those user data elements that you wish to modify in the request body. For example, if you only need to update the user's email, for don't include the other body parameters like ``id``, ``enabled``, or ``rax-auth:domainId``.

Users who hold the admin role can update users who hold the user role ( ``identity:default`` ) or the admin role ( ``identity:user-admin`` ) for the same tenant.

Administrators can change the default region for another user, but the new value must be one of the regions listed for a Cloud Compute endpoint in the service catalog.

Administrators can change a user default region, but the new value must be one of the regions listed for a Cloud Compute endpoint in the service catalog.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |Success. The tenant is   |
|                          |                         |authenticated.           |
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





This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|id                        |xsd:string *(Required)*  |The userID.              |
+--------------------------+-------------------------+-------------------------+
|name                      |xsd:string *(Required)*  |The user name. Thevalue  |
|                          |                         |must begin with an alpha |
|                          |                         |character.               |
+--------------------------+-------------------------+-------------------------+
|email                     |xsd:string *(Required)*  |The useremail.           |
+--------------------------+-------------------------+-------------------------+
|enabled                   |xsd:Boolean *(Required)* |Indicates whetherthe     |
|                          |                         |user is enabled (true)   |
|                          |                         |or disabled (false).     |
|                          |                         |Users cannot update      |
|                          |                         |the``enabled``status on  |
|                          |                         |their own account.       |
+--------------------------+-------------------------+-------------------------+
|RAX-AUTH:defaultRegion    |xsd:string *(Required)*  |The default region that  |
|                          |                         |the user is assigned to. |
|                          |                         |Must be one of the       |
|                          |                         |regions available in the |
|                          |                         |service catalog.         |
+--------------------------+-------------------------+-------------------------+
|OS-KSADM:password         |xsd:string *(Required)*  |A password string that   |
|                          |                         |meets the following      |
|                          |                         |criteria: Length must be |
|                          |                         |at least 8 characters;   |
|                          |                         |no maximum Can include   |
|                          |                         |uppercase, lower case,   |
|                          |                         |and numeric characters.  |
|                          |                         |Can start with or        |
|                          |                         |include any of the       |
|                          |                         |following special        |
|                          |                         |characters: ~ ! @ # $ ^  |
|                          |                         |& _ - + = `|\(){}[]:;"'  |
|                          |                         |< >,. ? Password cannot  |
|                          |                         |begin with a space, but  |
|                          |                         |it can contain a space.  |
+--------------------------+-------------------------+-------------------------+





**Example Update user request: XML**


.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <user xmlns="http://docs.openstack.org/identity/api/v2.0"
          xmlns:ns2="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
          xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
          id="123456" username="jqsmith"
          enabled="true"
          email="john.smith@example.org">
    </user>


**Example Update user request: JSON**


.. code::

    {
      "user": {
        "id": "123456",
        "username": "jqsmith",
        "email": "john.smith@example.org",
        "enabled": true
      }
    }


**Example Update user password request: XML**


.. code::

    <user username="abc123"  
        ns1:password="ungu355ab13" 
        xmlns:ns1="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0" 
        xmlns:ns2="http://docs.openstack.org/identity/api/v2.0" />


**Example Update user password request: JSON**


.. code::

    {
        "user": {
                "username": "abc123",  
                "OS-KSADM:password":"ungu355ab13"
            }
    }


Response
^^^^^^^^^^^^^^^^^^





**Example Update User Information And Password: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <user xmlns="http://docs.openstack.org/identity/api/v2.0"
          xmlns:ns2="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
          xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
          id="123456" username="jqsmith"
          enabled="true"
          email="john.smith@example.org"
          RAX-AUTH:defaultRegion="DFW"
          RAX-AUTH:domainId="5830280"
          RAX-AUTH:multiFactorEnabled="true" >
    </user>


**Example Update User Information And Password: JSON request**


.. code::

    {
      "user": {
      
        "id": "123456",
        "username": "jqsmith",
        "email": "john.smith@example.org",
        "enabled": true,
        "RAX-AUTH:defaultRegion":"DFW",
        "RAX-AUTH:domainId":"5830280",
        "RAX-AUTH:multiFactorEnabled": true
        
      }
    }

