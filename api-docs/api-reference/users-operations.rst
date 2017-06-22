.. _user-operations:

=====
Users
=====

Rackspace Cloud customers have :ref:`user <user-concept>` accounts that allow
them to access, configure, and  manage their Rackspace Cloud services and
account information. Each cloud account has  an :ref:`administrative owner
<auth-roles-svc-adm-usr>` (``user-admin``) and can also have  one or more
sub-user accounts that provide access to the Rackspace Cloud services available
on the account.

Use the following API operations to to create, review, update, and delete user
accounts,  account information, and account credentials.

.. contents::
   :local:
   :depth: 1

..  note::

     Some of the functionality described in this section is provided by the
     :ref:`OS-KSADM and RAX-KSKEY extensions <extensions-ovw>` to the
     core Identity API.

     When these requests are issued by an account user, they act only upon
     that account user. To learn more about Identity account users, see
     :ref:`Roles and role assignments <roles-and-role-assignments>`.

.. include:: methods/users/post-add-user-v2.0.rst
.. include:: methods/users/get-list-users-v2.0.rst
.. include:: methods/users/get-user-by-id-v2.0.rst
.. include:: methods/users/post-user-information-and-password-v2.0.rst
.. include:: methods/users/delete-a-user-v2.0.rst
.. include:: methods/users/get-accessible-domains-for-user-v2.0.rst
.. include:: methods/users/get-user-admin-v2.0.rst
.. include:: methods/users/post-add-credential-to-user-v2.0-users-userid-os-ksadm-credentials.rst
.. include:: methods/users/get-user-api-key-credentials-v2.0-users-userid-os-ksadm-credentials-rax-kskey.rst
.. include:: methods/users/post-reset-api-key-for-user-v2.0-users-userid-os-ksadm-credentials-rax-kskey.rst
.. include:: methods/users/post-forgot-pwd-v2.0.rst
.. include:: methods/users/post-reset-pwd-v2.0.rst
.. include:: methods/users/change-pwd-v2.0.rst
