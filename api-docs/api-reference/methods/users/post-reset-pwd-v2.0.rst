.. _post-reset-pwd-v2.0:

Reset password
~~~~~~~~~~~~~~~

.. code::

    POST /v2.0/users/RAX-AUTH/pwd-reset

Use the Reset Password operation to update user's password.

Request
-------

This table shows the header and URI parameters for the request:

.. csv-table::
   :header: Name, Type, Description
   :widths: 2, 2, 2

   X-Auth-Token, Header String *(Required)*, A valid password reset token.

This table shows the body parameters for the request:

.. csv-table::
   :header: Name, Type, Description
   :widths: 2, 2, 2

   RAX-AUTH:passwordReset, Object, Provides password to be updated.
   RAX-AUTH:passwordReset.\ **password**, String *(Required)*, New password for user.

**Example: Reset password: XML request**

.. code::

   POST /v2.0/users/RAX-AUTH/pwd-reset HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Content-Type: application/xml
   X-Auth-Token: APU9ymNjSKJG21HVdiRdOg0rk2fqh7uQ1FafVDXo3SId6nMHjUkKSDacFwDLGCC9U_DKI6Lwzu-wMi3LIWT-bA24EdGYdycM3rKzAfVPiCCjigN315ZLJo5s2TmiGQTSW9b5H7euQjJ6KBTk5elT2l8HrPH-9rrBjw

   <?xml version="1.0" encoding="UTF-8"?>
   <passwordReset password="superSecurePassw0rd!"
        xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
        xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
        xmlns:OS-KSCATALOG="http://docs.openstack.org/identity/api/ext/OS-KSCATALOG/v1.0"
        xmlns:atom="http://www.w3.org/2005/Atom" xmlns:identity="http://docs.openstack.org/identity/api/v2.0"/>

**Example: Reset password: JSON request**

.. code::

   POST /v2.0/users/RAX-AUTH/pwd-reset HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Content-Type: application/json
   X-Auth-Token: APU9ymNjSKJG21HVdiRdOg0rk2fqh7uQ1FafVDXo3SId6nMHjUkKSDacFwDLGCC9U_DKI6Lwzu-wMi3LIWT-bA24EdGYdycM3rKzAfVPiCCjigN315ZLJo5s2TmiGQTSW9b5H7euQjJ6KBTk5elT2l8HrPH-9rrBjw

   {
     "RAX-AUTH:passwordReset": {
       "password": "superSecurePassw0rd!"
     }
   }


Response
--------

This table shows the possible response headers for this operation:

.. csv-table::
   :header: Name, Type, Description
   :widths: 2, 2, 2

   X-User-Name, Header, Value for name provided on operation


This table shows the possible response codes for this operation:

.. csv-table::
   :header: Response Code, Name, Description
   :widths: 15 25 60

   204, No Content, No Content
   400, Bad Request, Password provided does not meet minimum requirements.
   401, Unauthorized, You are not authorized to complete this operation. This error can occur if the supplied token is determined to either not be issued by Rackspace or a Rackspace issued token that has been expired or revoked.
   403, Forbidden, "The request was valid, but the server is refusing to respond because the supplied token is a Rackspace issued token that is not expired or revoked, but is NOT a password reset token."
   404, Not Found, The requested resource was not found.

**Example: Reset password: response**

.. code::

   < HTTP/1.1 204 No Content
   < Vary:  Accept, Accept-Encoding, X-Auth-Token
   < X-User-Name: billybob
   < Content-Type: application/json
   < Server: Jetty(6.1.25)
