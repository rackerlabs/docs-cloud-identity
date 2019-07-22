.. _phone-pin-operations:

=========
Phone PIN
=========

When a customer calls into Rackspace, they will be required to give a 6 digit
phone PIN to the IVR or Support Racker to verify their identity. When a new user
is created, a 6 digit numeric phone PIN is assigned to the user by default. The
phone PIN cannot be deleted, however a user can update his phone PIN
using ``Update user information and password`` API.

**Update your own phone PIN**

.. include:: methods/users/post-user-information-and-password-v2.0.rst

**Retrieve your own phone PIN**

.. include:: methods/token/get-validate-token-v2.0-tokens-tokenid.rst
.. include:: methods/users/get-user-by-id-v2.0.rst
.. include:: methods/token/post-authenticate-as-tenant-with-token-v2.0-tokens.rst

**Use the following API operation to unlock your phone PIN**

.. include:: methods/phone-pin/unlock-phone-pin.rst

**Use the following API operation to reset the phone PIN of another user***

.. include:: methods/phone-pin/reset-phone-pin.rst
