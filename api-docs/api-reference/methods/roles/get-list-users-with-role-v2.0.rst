.. _get-list-users-with-role-v2.0:

List users with role
~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /v2.0/OS-KSADM/roles/{roleId}/RAX-AUTH/users

This operation returns a list of users with detailed account information about
each user, including email, name, user ID, phone pin state, account
configuration, and status information assigned to the specified role ID.

.. note::

  - Users with the ``identity:user-admin`` role can list sub-users within their
    domain that have the ``identity:manage`` role and ``identity:default`` role
    assigned to a specified role.

This table shows the possible response codes for this operation:

.. csv-table::
  :header: Response code, Name, Description
  :widths: 2, 2, 2

    200, OK, The request has succeeded.
    400, Bad Request, The request was invalid.
    401, Unauthorized, You are not authorized to complete this operation. This error can occur if the request is submitted with an invalid authentication token.
    403, Forbidden, Caller does not have an appropriate role.
    404, Not Found, The requested resource was not found.
    405, Invalid Method, The method specified in the request is not valid for the resource identified in the request URI.
    413, Over Limit, The number of items returned is above the allowed limit.
    503, Service Fault, Service is not available.


Request
-------

This table shows the header and URI parameters for the request:

.. csv-table::
  :header: Name, Type, Description
  :widths: 2, 2, 2

  X-Auth-Token, Header String *(Required)*, A valid authentication token.
  {roleId}, URI String *(Required)*, A role id assigned by a system when role is added.

This table shows the query parameters for the request:

.. csv-table::
  :header: Name, Type, Description
  :widths: 2, 2, 2

  limit, Int *(Optional)*, Requests a specified page size of returned items from the query. Returns a number of items up to the specified limit value. Use the ``limit`` parameter to make an initial limited request and use the ID of the last-seen item from the response as the ``marker`` parameter value in a subsequent limited request.
  marker, String *(Optional)*, Specifies the ID of the last-seen item. Use the ``limit`` parameter to make an initial limited request and use the ID of the last-seen item from the response as the ``marker`` parameter value in a subsequent limited request.


This operation does not accept a request body.

**Example: List users: HTTP request**

.. code::

   GET /v2.0/OS-KSADM/roles/10010175/RAX-AUTH/users HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/xml
   X-Auth-Token: 0cb090705e82443fa71471e9c3456789
   Content-type: application/xml


**Example: List users: HTTP request**


.. code::

   GET /v2.0/OS-KSADM/roles/10010175/RAX-AUTH/users HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/json
   X-Auth-Token: 0cb090705e82443fa71471e9c3456789
   Content-type: application/json


Response
--------

This table shows the body parameters for the response:

.. list-table::
  :widths: 40 20 40
  :header-rows: 1

  * - Name
    - Type
    - Description
  * - users
    - Object *(Required)*
    - Returns the collection of users who match the specification in the List
      user API request.
  * - users.\ **user**
    - Object *(Required)*
    - A user object that provides user account information.
  * - user.\ **RAX-AUTH:phonePinState**
    - String *(Required)*
    - The phone pin state.

      * ``INACTIVE`` The user does not have a phone pin.
      * ``LOCKED`` The user has a phone pin, but the pin has been locked due to
        excessive failed verification attempts. The user must unlock the pin
        before pin verifications can occur.
      * ``ACTIVE`` The user has a phone pin against which verifications can be
        performed.
  * - user.\ **RAX-AUTH:defaultRegion**
    - String *(Optional)*
    - The default region that the user is assigned to. Must be one of the
      regions available in the service catalog.
  * - user.\ **RAX-AUTH:domainId**
    - String *(Optional)*
    - The ID for the domain that the user account has been assigned to.
  * - user.\ **RAX-AUTH:multiFactorEnabled**
    - Boolean *(Optional)*
    - If an account has been configured to use multi-factor authentication,
      this field indicates if multi-factor authentication is currently
      enabled or disabled.
  * - user.\ **RAX-AUTH:multiFactorState**
    - String *(Optional)*
    - This extended attribute indicates if a multifactor-enabled user
      account is locked as a result of failed authentication attempts. If the
      account has been locked at any point, the value is either ``LOCKED`` or
      ``ACTIVE``. User administrators can use the Update multi-factor
      authentication settings on account operation to restore access to a
      locked account.
  * - user.\ **RAX-AUTH:userMultiFactorEnforcementLevel**
    - String *(Optional)*
    - If present, this extended attribute specifies the multi-factor
      authentication enforcement policy that applies to the specified account.

      * ``REQUIRED`` The user must use multi-factor authentication to log in to
        their Rackspace Cloud account.
      * ``OPTIONAL.`` The user has the option to authenticate using
        multi-factor authentication.
      * ``DEFAULT.`` The user multi-factor authentication requirements are
        determined by the domain level enforcement setting for multi-factor
        authentication.
  * - user.\ **RAX-AUTH:contactId**
    - String *(Optional)*
    - The core contact ID.
  * - user.\ **RAX-AUTH:passwordExpiration**
    - String *(Optional)*
    - If present, this extended attribute specifies the time when the
      user's current password will expire.

**Example List user with role: HTTP response**

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/xml


**Example List user with role: XML response**

.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <users
         xmlns:atom="http://www.w3.org/2005/Atom"
         xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
         xmlns="http://docs.openstack.org/identity/api/v2.0"
         xmlns:ns4="http://docs.rackspace.com/identity/api/ext/RAX-KSGRP/v1.0"
         xmlns:rax-ksqa="http://docs.rackspace.com/identity/api/ext/RAX-KSQA/v1.0"
         xmlns:os-ksadm="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
         xmlns:rax-kskey="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"
         xmlns:os-ksec2="http://docs.openstack.org/identity/api/ext/OS-KSEC2/v1.0" >

         <user
               rax-auth:domainId="5830280"
               rax-auth:defaultRegion="DFW"
               rax-auth:multiFactorEnabled="true"
               rax-auth:multiFactorState="ACTIVE"
               rax-auth:userMultiFactorEnforcementLevel="OPTIONAL"
               rax-auth:multi
               id="123456"
               username="jqsmith"
               email="john.smith@example.org"
               enabled="true"/>

         <user
               rax-auth:contactId="1234"
               rax-auth:domainId="5830280"
               rax-auth:defaultRegion="DFW"
               rax-auth:multiFactorEnabled="false"
               id="938439"
               username="poejo"
               email="poe.joe@object.org"
               enabled="true"/>
   </users>


**Example List user with role: HTTP response**

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json


**Example List user with role: JSON response**

.. code::

   {
     "users": [
       {
         "rax-auth:domainId":"5830280"
         "id": "123456",
         "enabled": true,
         "username": "jqsmith",
         "email": "john.smith@example.org",
         "rax-auth:defaultRegion":"DFW",
         "rax-auth:phonePinState": "ACTIVE",
         "rax-auth:multiFactorEnabled":"true",
         "rax-auth:multiFactorState":"ACTIVE",
         "rax-auth:userMultiFactorEnforcementLevel":"OPTIONAL"
       },
       {
         "rax-auth:contactId":"1234",
         "rax-auth:domainId":"5830280",
         "id": "938439",
         "enabled": false,
         "username": "poejo",
         "email": "poe.joe@example.org",
         "rax-auth:defaultRegion":"DFW",
         "rax-auth:multiFactorEnabled":"false"
         }
     ]
   }
