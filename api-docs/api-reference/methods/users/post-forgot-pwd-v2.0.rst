.. _post-forgot-pwd-v2.0:

Forgot password
~~~~~~~~~~~~~~~

.. code::

    POST /v2.0/users/RAX-AUTH/forgot-pwd

Use the Forgot password operation to get a password reset token delivered to
the email address associated with your account.

You can use the forgot password operation to reset the password through the
Rackspace Identity API or Rackspace Cloud user interface.

    - To reset the password by using the API, submit the forgot password
      request without the portal attribute. After you submit the request, the
      user receives an email that contains a reset password token with
      directions to use it in the :ref:`Reset password <post-reset-pwd-v2.0>`
      operation.

    - To reset the password through the user interface, include the
      portal attribute in the forgot password API request. After you
      submit the request, the user receives an email that contains a link to
      the Rackspace user interface to change the password.

.. note::

   - The reset token has a limited lifespan. If the reset operation fails,
     submit another forgot password request to generate a new token.

   - An email is only sent if the username matches the existing user.

   - Forgot password operation will always return 204.

   - Resetting the password through the user interface is a restricted feature
     for Rackspace administrator and support users.


Request
-------

This table shows the body parameters for the request:

.. csv-table::
   :header: Name, Type, Description
   :widths: 2, 2, 2

   RAX-AUTH:forgotPasswordCredentials, Object, Provides username and portal for forgot password.
   RAX-AUTH:forgotPasswordCredentials.\ **username**, String *(Required)*, The user name of the Rackspace Cloud account.
   RAX-AUTH:forgotPasswordCredentials.\ **portal**, String *(Optional)*, Authentication portal. This is a restricted value provided by Rackspace.

**Example: Forgot password: XML request**

.. code::

   POST /v2.0/users/RAX-AUTH/forgot-pwd HTTP/1.1
   Host: identity.api.rackspace.com
   Content-Type: application/xml

   <?xml version="1.0" encoding="UTF-8"?>
   <forgotPasswordCredentials username="billybob"
        xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
        xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
        xmlns:OS-KSCATALOG="http://docs.openstack.org/identity/api/ext/OS-KSCATALOG/v1.0"
        xmlns:atom="http://www.w3.org/2005/Atom"
        xmlns:identity="http://docs.openstack.org/identity/api/v2.0"/>

**Example: Forgot password: JSON request**

.. code::

   POST /v2.0/users/RAX-AUTH/forgot-pwd HTTP/1.1
   Host: identity.api.rackspace.com
   Content-Type: application/json

   {
     "RAX-AUTH:forgotPasswordCredentials": {
       "username": "billybob"
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
   :widths: 2, 2, 2

   204, No Content, No Content

**Example: Forgot password: response**

.. code::

   < HTTP/1.1 204 No Content
   < Vary:  Accept, Accept-Encoding, X-Auth-Token
   < X-User-Name: billybob
   < Content-Type: application/json
   < Server: Jetty(6.1.25)
