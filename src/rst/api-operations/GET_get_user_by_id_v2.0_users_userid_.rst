=============================================================================
Get User By Id -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Get User By Id
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_get_user_by_id_v2.0_users_userid_.rst#request>`__
`Response <GET_get_user_by_id_v2.0_users_userid_.rst#response>`__

.. code-block:: javascript

    GET /v2.0/users/{userId}

Get detailed account information for a specific user, by user id.

This request returns the following information for each account associated with the specified user id: email address, user name, user id, status, default region, and domain id.

If this request is issued by a user holding the admin role ( ``identity:user-admin`` ), the specific user's information is returned only if that user is associated with the same tenant as the requester's ``user-admin`` token.

If this request is issued by a user holding the user role ( ``identity:default`` ), information is returned for only the requester.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |The operation completed  |
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





**Example Get user by id: XML response**


.. code::

    HTTP/1.1 200 OK
    Content-Type: application/xml
    


**Example Get user by id: json response**


.. code::

    {
      "user": 
        {
          "rax-auth:domainId":"5830280"
          "id": "123456",
          "enabled": true,
          "username": "jqsmith",
          "email": "john.smith@example.org",
          "rax-auth:defaultRegion":"DFW",
          "rax-auth:multiFactorEnabled":"true",
          "rax-auth:multiFactorState":"ACTIVE",
          "rax-auth:userMultiFactorEnforcementLevel":"OPTIONAL"
        }
    }
    

