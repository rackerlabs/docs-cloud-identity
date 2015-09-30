.. _user-operations:

Users 
--------

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

- Add user 
- List users
- Get user by id
- Update user information and password 
- Deletes a user
- Get user admin 
- Add credential to user
- Get user credentials 
- Reset API key credentials

