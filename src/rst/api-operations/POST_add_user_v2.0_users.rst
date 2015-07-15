=============================================================================
Add User -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Add User
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <POST_add_user_v2.0_users.rst#request>`__
`Response <POST_add_user_v2.0_users.rst#response>`__

.. code-block:: javascript

    POST /v2.0/users

Adds a user.

User and Identity administrators can add accounts to an existing Rackspace Cloud account by using the Add user API operation. Administrators can add up to 100 users to an account.

In the Add user request, include the required values for the user name and email and specify optional attributes as needed.

You can specify an initial password for the user by including it in the request. If you don't specify a password, the Identity service generates one and returns it in the response. In either case, make a note of the password so you can provide it to the user. After the user is created, you cannot retrieve the password by any means. However, you can update the password by using the Update user API operation or by changing the value from the User Management page in the Cloud Control panel.

NotesUsers with the User Admin role can manage sub-user accounts through the API or from the `Cloud Control panel <https://mycloud.rackspace.com/cloud/929418/account#users>`__. Use the Control panel to add the user's full name, contact information, and configure account security.

If you try to create an account with the user name from an existing account, the Add user operation returns an ``HTTP error 409`` message.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|201                       |Created                  |The request has been     |
|                          |                         |fulfilled. The user has  |
|                          |                         |been created.            |
+--------------------------+-------------------------+-------------------------+
|409                       |Conflict                 |Indicates that the user  |
|                          |                         |you are trying to add    |
|                          |                         |already exists.          |
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
|X-Auth-Token              |xsd:string *(Required)*  |A valid admin            |
|                          |                         |authentication token.    |
+--------------------------+-------------------------+-------------------------+





This table shows the body parameters for the request:

+------------------------+------------------------+----------------------------+
|Name                    |Type                    |Description                 |
+========================+========================+============================+
|username                |xsd:string *(Required)* |The name to assign to the   |
|                        |                        |user. Specify a value that  |
|                        |                        |meets the following         |
|                        |                        |criteria: Start with an     |
|                        |                        |alpha character. Minimum    |
|                        |                        |length: 1 character Can     |
|                        |                        |contain upper and lowercase |
|                        |                        |characters. Can contain any |
|                        |                        |of the following special    |
|                        |                        |characters:. - @ _          |
+------------------------+------------------------+----------------------------+
|email                   |xsd:string *(Required)* |Email address for the user  |
|                        |                        |account,                    |
|                        |                        |``jqsmith@test.com`` for    |
|                        |                        |example.                    |
+------------------------+------------------------+----------------------------+
|enabled                 |xsd:bool *(Required)*   |Indicates whether the user  |
|                        |                        |can authenticate after the  |
|                        |                        |user account is created.If  |
|                        |                        |no value is specified, the  |
|                        |                        |default value is            |
|                        |                        |specified:``enabled=true``. |
+------------------------+------------------------+----------------------------+
|OS-KSADM:password       |xsd:string *(Required)* |Specify an initial password |
|                        |                        |for the user account. If    |
|                        |                        |this value is not           |
|                        |                        |specified, the Identity     |
|                        |                        |service automatically       |
|                        |                        |generates a password.       |
|                        |                        |Ensure that the value you   |
|                        |                        |specify meets the following |
|                        |                        |criteria: Length must be at |
|                        |                        |least 8 characters; no      |
|                        |                        |maximum. Can include        |
|                        |                        |uppercase, lower case, and  |
|                        |                        |numeric characters. Can     |
|                        |                        |start with or include any   |
|                        |                        |of the following special    |
|                        |                        |characters: ~ ! @ # % ^ & * |
|                        |                        |_ - | \ ( ) { } [ ] : ; " ' |
|                        |                        |< >,. ? / Password cannot   |
|                        |                        |begin with a space, but it  |
|                        |                        |can contain a space.        |
+------------------------+------------------------+----------------------------+





**Example Add User: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <user xmlns="http://docs.openstack..org/identity/api/v2.0"
          enabled="true" 
          email="newUserh@example.com"
          username="newUser"/>
    


**Example Add User: JSON request**


.. code::

    {
      "user": {
        "username": "newUser",
        "email": "newUser@example.com",
        "enabled": true
    	}
    }
    


**Example Add user with password request: XML**


.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <user xmlns:ns1="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0" 
        xmlns:ns2="http://docs.openstack.org/identity/api/v2.0"
        username="newUser" 
        email="newUser@example.com" 
        enabled="true" 
        ns1:password="Password48"/>


**Example Add user with password request: JSON**


.. code::

    {
        "user": {
                "username": "newUser", 
                "email": "newUser@example.com", 
                "enabled": true, 
                "OS-KSADM:password":"Password48"
            }
    }


Response
^^^^^^^^^^^^^^^^^^


This table shows the body parameters for the response:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|user                      |identity:User            |A ``user`` object that   |
|                          |*(Required)*             |contains the user        |
|                          |                         |account information.     |
|                          |                         |``{"user": {"username":  |
|                          |                         |"test", "OS-             |
|                          |                         |KSADM:password":         |
|                          |                         |"xxxxxxxx", "email":     |
|                          |                         |"jqsmith@test.com"}``    |
+--------------------------+-------------------------+-------------------------+
|RAX-AUTH:defaultRegion    |identity:User            |Specifies the default    |
|                          |*(Required)*             |region for the user      |
|                          |                         |account. This value is   |
|                          |                         |inherited from the user  |
|                          |                         |administrator when the   |
|                          |                         |account is created..     |
+--------------------------+-------------------------+-------------------------+
|RAX-AUTH:domainId         |identity:User            |Identifies the domain    |
|                          |*(Required)*             |that contains the user   |
|                          |                         |account. This value is   |
|                          |                         |inherited from the user  |
|                          |                         |administrator when the   |
|                          |                         |account is created.      |
+--------------------------+-------------------------+-------------------------+
|id                        |xsd:string *(Required)*  |A unique system-         |
|                          |                         |generated ID for the     |
|                          |                         |user account.The ID      |
|                          |                         |generated for the        |
|                          |                         |account cannot be        |
|                          |                         |modified.                |
+--------------------------+-------------------------+-------------------------+
|username                  |xsd:string *(Required)*  |The name that the user   |
|                          |                         |can use to authenticate  |
|                          |                         |to the Rackspace Cloud.  |
|                          |                         |You can change this      |
|                          |                         |value through the API or |
|                          |                         |the Cloud Control panel. |
+--------------------------+-------------------------+-------------------------+
|OS-KSADM:password         |xsd:string *(Required)*  |The password value that  |
|                          |                         |the user needs for       |
|                          |                         |authentication. If the   |
|                          |                         |Add user request         |
|                          |                         |included a password      |
|                          |                         |value, this attribute is |
|                          |                         |not included in the      |
|                          |                         |response.                |
+--------------------------+-------------------------+-------------------------+
|email                     |xsd:string *(Required)*  |Email address for the    |
|                          |                         |user account,            |
|                          |                         |``jqsmith@test.com`` for |
|                          |                         |example.                 |
+--------------------------+-------------------------+-------------------------+
|enabled                   |xsd:bool *(Required)*    |Indicates whether the    |
|                          |                         |user has permission to   |
|                          |                         |authenticateusing the    |
|                          |                         |user name and password   |
|                          |                         |credentials for the new  |
|                          |                         |user.This value defaults |
|                          |                         |to``enabled=true``.      |
+--------------------------+-------------------------+-------------------------+





**Example Add User: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <user xmlns="http://docs.openstack.org/identity/api/v2.0"
          xmlns:ns2="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
          xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
          id="123456" username="newUser"
          enabled="true"
          email="newUser@example.com"
          RAX-AUTH:defaultRegion="DFW"
          RAX-AUTH:domainId="5830280" >
    </user>


**Example Add User: JSON request**


.. code::

    {
      "user": {
        "RAX-AUTH:defaultRegion": "DFW",
        "RAX-AUTH:domainId": "5830280",
        "id": "123456",
        "username": "newUser",
        "email": "newUserh@example.com",
        "enabled": true
      }
    }

