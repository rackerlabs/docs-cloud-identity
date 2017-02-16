.. _post-create-user-v2.0-users:

Create user
~~~~~~~~~~~

.. code::

   POST /v2.0/users

Creates a Rackspace Cloud account user.

Users that have the ``identity:service-admin`` or ``identity:admin`` role can
use the  Create user operation to add a sub-user ( ``identity:default`` ) to a
Rackspace Cloud  account. Administrators can add up to 100 users to an account.

.. warning::

   Account sub-users created using the Add user operation can only access
   Rackspace Cloud  resources through the API. Only the Administrator user can
   access the account from the  Cloud Control panel. The Administrator user is
   assigned when the Rackspace Cloud account  is created during the Rackspace
   sign up process.

In the Create user request, include the required values for the user name,
email, and initial account status (``enabled=true`` or ``enabled=false``)
attributes.

Users inherit the domain and default region associated with the Rackspace
Cloud account.  They also inherit group membership. If you want to override a
default value, include the  new value in the Create user request.

You can also include values for optional attributes such as password and role.
Review the  following details for additional information about specifying
optional attributes.

password
   Use this parameter to specify an initial password for the user. If you
   don't specify a  password, Identity service automatically generates one and
   returns it in the response.  Make note of the password, so you can give it
   to the user. After the user is created,  the password cannot be retrieved
   by any means.

defaultRegion
   Specify this attribute to override the default region assigned to the user.
   Users can  change their default region by using the
   :ref:`post-update-user-information-and-password-v2.0>` API operation, but
   they can only change it to a region that is listed in the service catalog
   for the Cloud Servers service.

roles
   Use the roles attribute to assign a user one or more roles other than the
   default role ( ``identity:default`` ). You can also associate the user with
   a new tenant by specifying a new alphanumeric ``tenantId`` attribute in
   the ``role`` element. You cannot specify an existing an id for an existing
   tenant.

This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|201                       |Created                  |The request completed    |
|                          |                         |successfully.Location to |
|                          |                         |the URI of the newly     |
|                          |                         |created user             |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |The request is missing   |
|                          |                         |one or more elements, or |
|                          |                         |the values of some       |
|                          |                         |elements are invalid.    |
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |You are not authorized   |
|                          |                         |to complete this         |
|                          |                         |operation. This error    |
|                          |                         |can occur if the request |
|                          |                         |is submitted with an     |
|                          |                         |invalid authentication   |
|                          |                         |token.                   |
+--------------------------+-------------------------+-------------------------+
|403                       |Forbidden                |The request was valid,   |
|                          |                         |but the server is        |
|                          |                         |refusing to respond      |
|                          |                         |because you do not have  |
|                          |                         |permission to access the |
|                          |                         |requested resource.      |
|                          |                         |Submit a request to your |
|                          |                         |account administrator to |
|                          |                         |determine how to gain    |
|                          |                         |access.                  |
+--------------------------+-------------------------+-------------------------+
|405                       |Invalid Method           |The method specified in  |
|                          |                         |the request is not valid |
|                          |                         |for the resource         |
|                          |                         |identified in the        |
|                          |                         |request URI.             |
+--------------------------+-------------------------+-------------------------+
|413                       |Over Limit               |The number of items      |
|                          |                         |returned is above the    |
|                          |                         |allowed limit.           |
+--------------------------+-------------------------+-------------------------+
|415                       |Bad Media Type           |Bad media type. This may |
|                          |                         |result if the wrong      |
|                          |                         |media type is used in    |
|                          |                         |the API request. Check   |
|                          |                         |the content-type and     |
|                          |                         |accept headers included  |
|                          |                         |in the request.          |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Fault            |Service is not available.|
+--------------------------+-------------------------+-------------------------+


Request
-------

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|X-Auth-Token              |String *(Required)*      |A valid admin            |
|                          |                         |authentication token.    |
+--------------------------+-------------------------+-------------------------+


This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|user                      |Object                   |Specifies the user       |
|                          |                         |information to update.   |
+--------------------------+-------------------------+-------------------------+
|user.\                    |String *(Optional)*      |Specify the default      |
|**RAX-AUTH:defaultRegion**|                         |region for the user:     |
|                          |                         |``DFW``, ``IAD``,        |
|                          |                         |``HKG``, or ``SYD``.     |
+--------------------------+-------------------------+-------------------------+
|user.\                    |String *(Required)*      |To assign the user to a  |
|**RAX-AUTH:domainId**     |                         |domain, specify the      |
|                          |                         |domain ID. If you don't  |
|                          |                         |know the domain ID, use  |
|                          |                         |the Retrieve domains     |
|                          |                         |operation to list the    |
|                          |                         |available domains.       |
+--------------------------+-------------------------+-------------------------+
|user.\                    |String *(Required)*      |The name to assign to    |
|**name**                  |                         |the user. Specify a      |
|                          |                         |value that meets the     |
|                          |                         |following criteria: *    |
|                          |                         |Start with an alpha      |
|                          |                         |character. * Minimum     |
|                          |                         |length: 1 character *    |
|                          |                         |Can contain upper and    |
|                          |                         |lowercase characters. *  |
|                          |                         |Can contain any of the   |
|                          |                         |following special        |
|                          |                         |characters:., (period),  |
|                          |                         |- (hyphen), @,           |
|                          |                         |_ (underscore)           |
+--------------------------+-------------------------+-------------------------+
|user.**email**            |String *(Required)*      |The user email.          |
+--------------------------+-------------------------+-------------------------+
|user.**enable**           |Bool *(Required)*        |Indicates whether the    |
|                          |                         |user is enabled (true)   |
|                          |                         |or disabled (false).     |
+--------------------------+-------------------------+-------------------------+
|user.**OS-KSADM:password**|String *(Optional)*      |Specify a password       |
|                          |                         |string that meets the    |
|                          |                         |following criteria: *    |
|                          |                         |Length must be at least  |
|                          |                         |8 characters; no maximum |
|                          |                         |* Includes at least one  |
|                          |                         |uppercase and one lower  |
|                          |                         |case character * Can     |
|                          |                         |include special          |
|                          |                         |characters. * Password   |
|                          |                         |cannot begin with a      |
|                          |                         |space.                   |
+--------------------------+-------------------------+-------------------------+
|user.**roles**            |Rolelist *(Optional)*    |The roles object assigns |
|                          |                         |the user roles. For each |
|                          |                         |role, specify the name   |
|                          |                         |of an existing role      |
|                          |                         |using the ``role``       |
|                          |                         |element with the         |
|                          |                         |``name`` attribute. You  |
|                          |                         |can also specify a       |
|                          |                         |``tenantId`` attribute   |
|                          |                         |to assign a role to a    |
|                          |                         |new tenant container.    |
|                          |                         |See the XML and JSON     |
|                          |                         |request examples for the |
|                          |                         |correct syntax. You can  |
|                          |                         |only specify a new       |
|                          |                         |``tenantId`` in this     |
|                          |                         |field.                   |
+--------------------------+-------------------------+-------------------------+
|user.**RAX-KSGRP:groups** |String *(Optional)*      |This object defines the  |
|                          |                         |groups the user belongs  |
|                          |                         |to. For each group,      |
|                          |                         |specify the              |
|                          |                         |``RAX-KSGRP:group``      |
|                          |                         |element with the ``name``|
|                          |                         |``name`` attribute. See  |
|                          |                         |the XML and JSON request |
|                          |                         |examples for the correct |
|                          |                         |syntax.                  |
+--------------------------+-------------------------+-------------------------+
|user.**RAX-KSQA:secretQA**|String *(Optional)*      |This object specifies    |
|                          |                         |the secret ``question``  |
|                          |                         |and ``answer``           |
|                          |                         |attributes that can be   |
|                          |                         |used to verify the       |
|                          |                         |identity of the user.    |
+--------------------------+-------------------------+-------------------------+


**Example:  Create user request: XML**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <user OS-KSADM:password="securePassword" RAX-AUTH:defaultRegion="SYD"
        RAX-AUTH:domainId="5473387" email="john.smith@example.org"
        enabled="true" username="jqsmith"
        xmlns="http://docs.openstack.org/identity/api/v2.0"
        xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
        xmlns:RAX-AUTH="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
        xmlns:RAX-KSGRP="http://docs.rackspace.com/identity/api/ext/RAX-KSGRP/v1.0"
        xmlns:RAX-KSQA="http://docs.rackspace.com/identity/api/ext/RAX-KSQA/v1.0"
        xmlns:atom="http://www.w3.org/2005/Atom">
        <roles>
             <role name="managed"/>
        </roles>
        <RAX-KSGRP:groups>
             <RAX-KSGRP:group name="restricted"/>
        </RAX-KSGRP:groups>
        <RAX-KSQA:secretQA answer="There is no meaning" question="What is the meaning of it all"/>
   </user>





**Example:  Create user request: JSON**


.. code::

   {
     "user": {
       "RAX-AUTH:domainId": "5473387",
       "enabled": true,
       "username": "jqsmith",
       "OS-KSADM:password": "securePassword",
       "email": "john.smith@example.org",
       "roles": [
         {
           "name": "managed",
           "tenantId": "newTenantId"
         }
       ],
       "RAX-KSGRP:groups": [
         {
           "name": "restricted"
         }
       ],
       "RAX-AUTH:defaultRegion": "SYD",
       "RAX-KSQA:secretQA": {
         "answer": "There is no meaning",
         "question": "What is the meaning of it all"
       }
     }
   }


Response
--------


This table shows the header parameters for the response:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|Location                  |String *(Required)*      |Location to the URI of   |
|                          |                         |the newly created user   |
+--------------------------+-------------------------+-------------------------+


**Example:  Create user: XML response**

.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <user OS-KSADM:password="securePassword" RAX-AUTH:defaultRegion="SYD"
        RAX-AUTH:domainId="5473387" email="john.smith@example.org"
        enabled="true" username="jqsmith"
        xmlns="http://docs.openstack.org/identity/api/v2.0"
        xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
        xmlns:RAX-AUTH="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
        xmlns:RAX-KSGRP="http://docs.rackspace.com/identity/api/ext/RAX-KSGRP/v1.0"
        xmlns:RAX-KSQA="http://docs.rackspace.com/identity/api/ext/RAX-KSQA/v1.0"
        xmlns:atom="http://www.w3.org/2005/Atom">
        <roles>
             <role name="managed"  tenantId="newTenantId"/>
        </roles>
        <RAX-KSGRP:groups>
             <RAX-KSGRP:group name="restricted"/>
        </RAX-KSGRP:groups>
        <RAX-KSQA:secretQA answer="There is no meaning" question="What is the meaning of it all"/>
   </user>


**Example:  Create user: JSON response**

.. code::

   {
     "user": {
       "RAX-AUTH:domainId": "5473387",
       "id": "123456",
       "enabled": true,
       "username": "jqsmith",
       "OS-KSADM:password": "securePassword",
       "email": "john.smith@example.org",
       "roles": [
         {
           "id": "278434",
           "name": "managed"
         }
       ],
       "RAX-KSGRP:groups": [
         {
           "id": "99823",
           "name": "restricted",
           "tenantId": "newtenantId"
         }
       ],
       "RAX-AUTH:defaultRegion": "SYD",
       "RAX-KSQA:secretQA": {
         "answer": "There is no meaning",
         "question": "What is the meaning of it all"
       }
     }
   }
