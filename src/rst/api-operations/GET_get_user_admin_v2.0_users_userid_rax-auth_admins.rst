=============================================================================
Get User Admin -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Get User Admin
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_get_user_admin_v2.0_users_userid_rax-auth_admins.rst#request>`__
`Response <GET_get_user_admin_v2.0_users_userid_rax-auth_admins.rst#response>`__

.. code-block:: javascript

    GET /v2.0/users/{userId}/RAX-AUTH/admins

Get the user administrator or point of contact for an account

Account users with the ``identity:user-admin`` or ``identity:default`` role can use this operation to identify the administrator or point of contact for a user account if they have questions or need assistance regarding user and/or role management. This request returns the following identifying information about the administrator: domain name, domain ID, email address, status, user ID and user name.



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





**Example Get User Admin: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <users xmlns="http://docs.openstack.org/identity/api/v2.0" 
        xmlns:ns2="http://www.w3.org/2005/Atom"
        xmlns:os-ksadm="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0" 
        xmlns:rax-ksqa="http://docs.rackspace.com/identity/api/ext/RAX-KSQA/v1.0" 
        xmlns:rax-kskey="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0" 
        xmlns:os-ksec2="http://docs.openstack.org/identity/api/ext/OS-KSEC2/v1.0" 
        xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0">
        <user id="10022879" 
            username="JuserAdmin" 
            enabled="true" 
            display-name="JuserAdmin" 
            rax-auth:defaultRegion="USA" 
            rax-auth:domainId="5701091"/>
    </users>


**Example Get User Admin: JSON request**


.. code::

    {
        "users": [
            {
                "RAX-AUTH:defaultRegion": "",
                "RAX-AUTH:domainId": "12345",
                "email": "userAdmin@rack.com",
                "enabled":"true",
                "id": "10022879",
                "username": "JuserAdmin"
            }
        ]
    }

