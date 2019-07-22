.. _post-update-user-information-and-password-v2.0:

Update user information and password
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /v2.0/users/{userId}

This operation updates the user information for the account associated with the
specified  user id. Before you submit the update request, use the :ref:`Get
user by id <get-user-by-id-v2.0>`  operation to verify that the user name,
email account, and status associated with ``userId``  match the account you
want to update.

Only include those user data elements that you wish to modify in the request
body.  For example, if you only need to update the user's email, for don't
include the other  body parameters like ``id``, ``enabled``, or
``rax-auth:domainId``.

.. note::

    -  Users who hold the admin role can update users who hold the user role
       (``identity:default``) or the admin role (``identity:user-admin``) for
       the same tenant.

    - Users with the ``identity:user-admin`` or ``identity:user-manage``
      role can update user information for users within their domain and with
      the ``identity:default`` role.

    -  Administrators can change the default region for another user, but the
       new value must be one of the regions listed for a Cloud Compute
       endpoint in the service catalog.

    -  Administrators can change a user default region, but the new value must
       be one of the regions listed for a Cloud Compute endpoint in the
       service catalog.

    - Only users with the ``identity:service-admin`` or ``identity:admin``
      role are allowed to update a user's ``RAX-AUTH:contactId``.

    - Only the ``RAX-AUTH:contactId`` attribute can be updated for a federated
      user.

    - The ``RAX-AUTH:phonePin`` is only returned if the caller is updating
      their own user account and a phone PIN exists on the account.


This table shows the possible response codes for this operation:

.. csv-table::
   :header: Response code, Name, Description
   :widths: auto

   200, OK, The request has been fulfilled. The user has been updated.
   400, Bad Request, "The request is missing one or more elements, or
   the values of some elements are invalid."
   401, Unauthorized, "You are not authorized to complete this operation.
   This error can occur if the request is submitted with an invalid
   authentication token."
   403, Forbidden, "The request was valid, but the server is refusing to
   respond because you do not have permission to access the requested
   resource. Submit a request to your account administrator to
   determine how to gain access."
   404, Not Found, The requested resource was not found.
   405, Invalid Method, "The method specified in the request is not valid for
   the resource identified in the request URI."
   406, Not Acceptable, The server cannot send data in a format requested.
   413, Over Limit, The number of items returned is above the allowed limit.
   503, Service Fault, Service is not available.

Request
-------

This table shows the header parameters for the request:

.. csv-table::
   :header: Name, Type, Description
   :widths: auto

   X-Auth-Token, String *(Required)*, A valid authentication token.
   {userId}, String *(Required)*, "A user ID assigned by system when a user is
   added."

This table shows the URI parameters for the request:

.. csv-table::
   :header: Name, Type, Description
   :widths: auto

   {userId}, String *(Required)*, "A user ID assigned by system when a user is
   created."

This table shows the body parameters for the request:

.. csv-table::
   :header: Name, Type, Description
   :widths: auto

   **user**, Object, "A ``user`` object that specifies the user account
   information."
   user.\ **username**, String *(Optional)*, The name to assign to the user.
   user.\ **email**, String *(Optional)*, Email address for the user account.
   user.\ **enabled**, String *(Optional)*, "Indicates whether the user is
   enabled (true) or disabled (false). Users cannot update the ``enabled``
   status on their own account."
   user.\ **RAX-AUTH:defaultRegion**, String *(Optional)*, "The default region
   that the user is assigned to. Must be one of the regions available in the
   service catalog."
   user.\ **RAX-AUTH:phonePin**, String *(Optional)*, "Specify a new phone PIN
   for the user account.  Ensure that the value specified meets the following
   criteria:

   - Use six numeric digits (such as 871694). A phone PIN cannot include more
     than three repeating numbers. (444 is OK, but 4444 is not.) A phone PIN
     cannot include more than three sequential numbers. (234 is OK, but 2345
     is not.)"
   user.\ **OS-KSADM:password**, String *(Optional)*, "Specify a new password
   for the user account. Ensure that the value specified meets the following
   criteria:

   - Password must be at least 8 characters in length, must contain at least
     one uppercase letter, one lowercase letter, and one numeric character."
   user.\ **RAX-AUTH:contactId**, String *(Optional)*, The core contact ID.


**Example:  Update user HTTP request header: XML**


.. code::

   POST /v2.0/users/123456 HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/xml
   Content-type: application/xml
   X-Auth-Token: eaf8345057414cd397d0543123456789


**Example:  Update user HTTP request header: JSON**


.. code::

   POST /v2.0/users/123456 HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/json
   Content-type: application/json
   X-Auth-Token: eaf8345057414cd397d0543123456789


**Example:  Update user request: XML**

.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <user xmlns="http://docs.openstack.org/identity/api/v2.0"
         xmlns:ns2="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
         xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
         username="jqsmith"
         enabled="true"
         email="john.smith@example.org"
         RAX-AUTH:contactId="12345">
   </user>


**Example:  Update user request: JSON**


.. code::

   {
     "user": {
       "username": "jqsmith",
       "email": "john.smith@example.org",
       "enabled": true,
       "RAX-AUTH:contactId": "1234"
     }
   }

**Example:  Update user password HTTP request header: XML**


.. code::

   POST /v2.0/users/123456 HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/xml
   Content-type: application/xml
   X-Auth-Token: eaf8345057414cd397d0543123456789


**Example:  Update user password HTTP request header: JSON**


.. code::

   POST /v2.0/users/123456 HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/xml
   Content-type: application/json
   X-Auth-Token: eaf8345057414cd397d0543123456789


**Example:  Update user password request: XML**


.. code::

   <user username="abc123"
       ns1:password="ungu355ab13"
       xmlns:ns1="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
       xmlns:ns2="http://docs.openstack.org/identity/api/v2.0" />


**Example:  Update user password request: JSON**


.. code::

   {
       "user": {
               "username": "abc123",
               "OS-KSADM:password":"ungu355ab13"
           }
   }


Response
--------

**Example:  Update user information and password: XML response**


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
         RAX-AUTH:phonePin="125897"
         RAX-AUTH:contactId="1234"
         RAX-AUTH:multiFactorEnabled="true" >
   </user>


**Example:  Update user information and password: JSON response**


.. code::

   {
     "user": {

       "id": "123456",
       "username": "jqsmith",
       "email": "john.smith@example.org",
       "enabled": true,
       "RAX-AUTH:defaultRegion":"DFW",
       "RAX-AUTH:domainId":"5830280",
       "RAX-AUTH:phonePin":"136983",
       "RAX-AUTH:multiFactorEnabled": true,
       "RAX-AUTH:contactId":"1234"
     }
   }
