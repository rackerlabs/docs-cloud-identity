.. _token-operations:

=====================
Authentication Tokens 
=====================

The Rackspace Cloud Identity service service provides
authentication services for the Rackspace Cloud. To gain access, users
and administrators can use the **POST tokens** operation to request an
authentication token from the Identity service, or generate a new token
after a previously issued token has expired. In subsequent requests to
Identity service or other services, clients include the authentication
token in the HTTP x-header parameter defined as ``X-Auth-Token`` to
verify identity and confirm access rights and privileges.

Authentication requests include credentials that verify the identity and
access permissions of the user making the request. Credentials can include
any of the following types:

-  Password credentials: user name and password

-  API Key credentials: user name and API key

-  Token and tenant Id or tenant name (requires Administrator
   privileges).

-  Passcode credentials: multi-factor authentication session ID and
   passcode values

Tenant information is required if you use the token method. You might
also need to include either the ``tenantId`` or ``tenantName`` on
authentication requests with API key or password credentials. Some
services use multi-level authentication, with service-specific
credentials in addition to vendor-specific credentials. In such cases,
associating a user with a tenant can be a method of passing that
additional level of identifying information to the service. Also, if a
user account is assigned to multiple tenants, then including the tenant
information generates the authentication token for the specified tenant.

Use the following token API operations to submit authentication requests and
manage tokens.

.. contents::
   :depth: 1
   :local:

..  note::

     Some of the functionality described in this section is provided by the
     :ref:`OS-KSADM and RAX-AUTH extensions <extensions-ovw>` to the
     core Identity API.

.. include:: methods/token/post-authenticate-as-user-with-password-or-api-key-v2.0-tokens.rst
.. include:: methods/token/post-authenticate-as-tenant-with-token-v2.0-tokens.rst
.. include:: methods/token/post-authenticate-with-multi-factor-authentication-passcode-credentials-v2.0-tokens.rst
.. include:: methods/token/get-validate-token-v2.0-tokens-tokenid.rst
.. include:: methods/token/delete-revoke-token-v2.0-tokens.rst
