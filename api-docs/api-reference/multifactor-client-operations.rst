.. _multifactor-operations:

===========================
Multi-factor authentication
===========================

Use the following multi-factor authentication API operations to configure and
manage multi-factor authentication settings for
Rackspace Cloud Accounts. For more information, see :ref:`Using multi-factor
authentication <multifactor-authenication-ovw>`.

.. contents::
   :local:
   :depth: 1

..  note::

  - Users can always use the MFA services on themselves.

  - Users with the ``identity:service-admin`` role can preform MFA operations
    for users with the ``identity:admin`` role, users with the
    ``identity:user-admin`` role, and sub-users.

  - Users with the ``identity:admin`` role can preform MFA operations for users
    with the ``identity:user-admin`` role and sub-users.

  - Users with the ``identity:user-admin`` or ``identity:user-manage`` role can
    preform MFA operations for users within their domain and with the
    ``identity:default`` role.

The functionality described in this section is provided by the
    :ref:`RAX-AUTH extension <extensions-ovw>`.

.. include:: methods/multifactor-auth/post-add-a-mobile-phone-v2.0.rst
.. include:: methods/multifactor-auth/post-sends-a-verification-code-to-a-phone-v2.0.rst
.. include:: methods/multifactor-auth/post-verifies-a-mobile-phone-v2.0.rst
.. include:: methods/multifactor-auth/get-mfa-phone-deviceid-v2.0.rst
.. include:: methods/multifactor-auth/get-multi-factor-phones-for-user-v2.0.rst
.. include:: methods/multifactor-auth/delete-remove-phone-from-account-v2.0.rst
.. include:: methods/multifactor-auth/post-add-an-otp-device-v2.0.rst
.. include:: methods/multifactor-auth/post-verifies-an-otp-device.rst
.. include:: methods/multifactor-auth/get-otp-device-by-id-v2.0.rst
.. include:: methods/multifactor-auth/get-otp-devices-for-account-v2.0.rst
.. include:: methods/multifactor-auth/delete-an-otp-device-from-account-v2.0.rst
.. include:: methods/multifactor-auth/put-update-multifactor-settings-on-account-v2.0.rst
.. include:: methods/multifactor-auth/post-generate-bypass-codes-v2.0.rst
.. include:: methods/multifactor-auth/put-update-domain-enforcement-setting-v2.0.rst
.. include:: methods/multifactor-auth/delete-mutlifactor-authentication-from-account-v2.0.rst
