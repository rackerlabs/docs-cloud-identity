=============================================================================
List Users -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

List Users
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_list_users_v2.0_users.rst#request>`__
`Response <GET_list_users_v2.0_users.rst#response>`__

.. code-block:: javascript

    GET /v2.0/users

Lists users.

This operation returns a list of users with detailed account information about each user including email, name, user ID, account configuration and status information. NotesIf this request is issued by a user holding the Identity admin role ( ``identity:user-admin`` ), it returns a list of all users for the tenant. To find a single user, include the ``name`` in the request. If this request is issued by a user holding the Identity user role ( ``identity:default`` ), the operation only returns information about the user account. To find the user with the authority to modify account permissions, refer to `"Get User Admin." <GET_getUserAdmin_v2.0_admins_User_Calls.html>`__



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |The request has          |
|                          |                         |succeeded.               |
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



This table shows the query parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|name                      |xsd:string *(Required)*  |Specify the user name to |
|                          |                         |look up.                 |
+--------------------------+-------------------------+-------------------------+
|email                     |xsd:string *(Required)*  |Specify the email        |
|                          |                         |address to look up.      |
+--------------------------+-------------------------+-------------------------+







**Example List Users: XML request**


.. code::

    GET /v2.0/users/12342b4ddb594819b697d0048614c117 HTTP/1.1
    Host: identity.api.rackspacecloud.com
    Accept: application/json
    X-Auth-Token: 0cb090705e82443fa71471e9c3456789
    Content-type: application/xml
    


**Example List Users: JSON request**


.. code::

    GET /v2.0/users/12342b4ddb594819b697d0048614c117 HTTP/1.1
    Host: identity.api.rackspacecloud.com
    Accept: application/json
    X-Auth-Token: 0cb090705e82443fa71471e9c3456789
    Content-type: application/json
    


Response
^^^^^^^^^^^^^^^^^^


This table shows the body parameters for the response:

+-------------------------------------+-------------+---------------------------------------+
|Name                                 |Type         |Description                            |
+=====================================+=============+=======================================+
|users                                |object       |Returns the collection of users who    |
|                                     |*(Required)* |match the specification in the List    |
|                                     |             |user API request.                      |
+-------------------------------------+-------------+---------------------------------------+
|user                                 |object       |A user object that provides user       |
|                                     |*(Required)* |account information:                   |
+-------------------------------------+-------------+---------------------------------------+
|RAX-AUTH:defaultRegion               |string       |The default region that the user is    |
|                                     |*(Required)* |assigned to. Must be one of the        |
|                                     |             |regions available in the service       |
|                                     |             |catalog.                               |
+-------------------------------------+-------------+---------------------------------------+
|RAX-AUTH:domainId                    |string       |The ID for the domain that the user    |
|                                     |*(Required)* |account has been assigned to.          |
+-------------------------------------+-------------+---------------------------------------+
|RAX-AUTH:multiFactorEnabled          |Boolean      |If an account has been configured to   |
|                                     |*(Required)* |use multi-factor authentication, this  |
|                                     |             |field indicates whether multi-factor   |
|                                     |             |authentication is currently enabled or |
|                                     |             |disabled.                              |
+-------------------------------------+-------------+---------------------------------------+
|RAX-AUTH:multiFactorState            |string       |This extended attribute indicates      |
|                                     |*(Required)* |whether a multifactor-enabled user     |
|                                     |             |account is locked as a result of       |
|                                     |             |failed authentication attempts. If the |
|                                     |             |account has been locked at any point,  |
|                                     |             |the value is either ``LOCKED`` or      |
|                                     |             |``ACTIVE``. User administrators can    |
|                                     |             |use the Update multi-factor            |
|                                     |             |authentication settings on account     |
|                                     |             |operation to restore access to a       |
|                                     |             |locked account.                        |
+-------------------------------------+-------------+---------------------------------------+
|RAX-                                 |string       |If present, this extended attribute    |
|AUTH:userMultiFactorEnforcementLevel |*(Required)* |specifies the multi-factor             |
|                                     |             |authentication enforcement policy that |
|                                     |             |applies to the specified account.      |
|                                     |             |``REQUIRED`` The user must use multi-  |
|                                     |             |factor authentication to log in to     |
|                                     |             |their Rackspace Cloud account. `domain |
|                                     |             |enforcement                            |
|                                     |             |<PUT_updateMultiFactorDomain_v2.0_RAX- |
|                                     |             |AUTH_domains__domainId__multi-         |
|                                     |             |factor_.html>`__ domain level          |
|                                     |             |enforcement is configured as           |
|                                     |             |``Optional``. ``OPTIONAL.`` The user   |
|                                     |             |has the option to authenticate using   |
|                                     |             |multi-factor authentication.           |
|                                     |             |``DEFAULT.`` The user multi-factor     |
|                                     |             |authentication requirements are        |
|                                     |             |determined by the domain level         |
|                                     |             |enforcement setting for multi-factor   |
|                                     |             |authentication.                        |
+-------------------------------------+-------------+---------------------------------------+





**Example List Users: XML request**


.. code::

    HTTP/1.1 200 OK
    Content-Type: application/xml
    


**Example List Users: JSON request**


.. code::

    HTTP/1.1 200 OK
    Content-Type: application/json
    

