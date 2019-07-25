.. _phone-pin-operations:

===========
Support PIN
===========

When a customer calls or chats with Rackspace Support, they must give a 6-
digit Support PIN to the Interactive Voice Response (IVR) system or to the
Support Racker
to verify their identity. When a new user is created, a 6-digit numeric phone
PIN is assigned to the user by default. The Support PIN cannot be deleted.
However, a user can update their Support PIN by using the
:ref:`Update user information and password <post-update-user-information-and-password-v2.0>` operation.

**Update your own Support PIN**


To update your own Support PIN, use the following operation:

- :ref:`Update user information and password <post-update-user-information-and-password-v2.0>`

**Retrieve your own Support PIN**


To retrieve your own Support PIN, see the following operations:

- :ref:`Validate token <get-validate-token-v2.0>`
- :ref:`Get user by id <get-user-by-id-v2.0>`
- :ref:`Authenticate as tenant with token <post-authenticate-as-tenant-with-token-v2.0>`

**Unlock your own Support PIN**


To unlock your Support PIN, use the following operation:

- :ref:`Unlock the Support PIN <unlock-phone-pin>`

**Reset the Support PIN of another user**


To reset the Support PIN of another user, use the following operation:

- :ref:`Reset the Support PIN <reset-phone-pin>`


.. include:: methods/users/post-user-information-and-password-v2.0.rst
.. include:: methods/token/get-validate-token-v2.0-tokens-tokenid.rst
.. include:: methods/users/get-user-by-id-v2.0.rst
.. include:: methods/token/post-authenticate-as-tenant-with-token-v2.0-tokens.rst
.. include:: methods/phone-pin/unlock-phone-pin.rst
.. include:: methods/phone-pin/reset-phone-pin.rst
