.. _user-operations:

Users 
--------

.. contents::
   :local:
   :depth: 1

Rackspace Cloud customers have :ref:`user <user-concept>` accounts that allow them to access, configure, and 
manage their Rackspace Cloud services and account information. Each cloud account has 
an :ref:`administrative owner <auth-roles-svc-adm-usr>` (``user-admin``) and can also have 
one or more sub-user accounts that provide access to the Rackspace Cloud services available 
on the account.  

Use the following API operations to to create, review, update, and delete user accounts, 
account information, and account credentials. 

..  note::
 
	Some of the functionality described in this section is provided by the
	:ref:`OS-KSADM and RAX-KSKEY extensions <extensions-ovw>` to the
	core Identity API.

	When these requests are issued by an account user, they act only upon
	that account user. To learn more about Identity account users, see
	:ref:`Roles and role assignments <auth-roles-and-assignments>`.

**API operations**

.. include:: methods/users/post-add-user-v2.0-users.rst 
.. include:: methods/users/get-list-users-v2.0-users.rst
.. include:: methods/users/get-get-user-by-id-v2.0-users-userid.rst
.. include:: methods/users/post-update-user-information-and-password-v2.0-users-userid.rst
.. include:: methods/users/delete-deletes-a-user-v2.0-users-userid.rst
.. include:: methods/users/get-get-user-admin-v2.0-users-userid-rax-auth-admins.rst
.. include:: methods/users/post-add-credential-to-user-v2.0-users-userid-os-ksadm-credentials.rst
- Get user credentials 
- Reset API key credentials




