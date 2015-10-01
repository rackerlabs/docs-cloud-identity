
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _put-updates-multi-factor-authentication-settings-on-account-v2.0-users-userid-rax-auth-multi-factor:

Updates multi-factor authentication settings on account
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    PUT /v2.0/users/{userId}/RAX-AUTH/multi-factor

Updates the multi-factor authentication settings for the specified account.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|204                       |No content               |The request succeeded.   |
|                          |                         |The server fulfilled the |
|                          |                         |request but does not     |
|                          |                         |need to return a body.   |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |Possible reasons: No     |
|                          |                         |multi-factor device on   |
|                          |                         |user account; multi      |
|                          |                         |factor phone on account  |
|                          |                         |is not verified.         |
+--------------------------+-------------------------+-------------------------+
|403                       |Forbidden                |Possible reasons: No     |
|                          |                         |multi-factor device on   |
|                          |                         |user account; multi      |
|                          |                         |factor phone on account  |
|                          |                         |is not verified.         |
+--------------------------+-------------------------+-------------------------+
|500                       |Service Fault            |Problem linking phone    |
|                          |                         |with Identity service    |
|                          |                         |multi-factor             |
|                          |                         |authentication service.  |
|                          |                         |Contact the Identity     |
|                          |                         |service service          |
|                          |                         |administrator for help.  |
+--------------------------+-------------------------+-------------------------+


Request
""""""""""""""""




This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{userId}                  |String                   |The unique, system-      |
|                          |                         |generated user ID for an |
|                          |                         |account.                 |
+--------------------------+-------------------------+-------------------------+
|X-Auth-Token              |String *(Required)*      |A valid authentication   |
|                          |                         |token.                   |
+--------------------------+-------------------------+-------------------------+





This table shows the body parameters for the request:

+-------------------------------------+-------------+---------------------------------------+
|Name                                 |Type         |Description                            |
+=====================================+=============+=======================================+
|enabled                              |Boolean      |A Boolean value that indicates whether |
|                                     |*(Optional)* |the account is enabled for multi-      |
|                                     |             |factor authentication. Specify         |
|                                     |             |``enabled=true`` to add support for    |
|                                     |             |multi-factor authentication;           |
|                                     |             |``enabled=false`` to disable it. When  |
|                                     |             |you enable multi-factor authentication,|
+-------------------------------------+-------------+---------------------------------------+
|RAX-                                 |String       |Specifies the user enforcement level   |
|AUTH:userMultiFactorEnforcementLevel |*(Optional)* |for multi-factor authentication: *     |
|                                     |             |``REQUIRED`` The user must use multi-  |
|                                     |             |factor authentication to log in to     |
|                                     |             |their Rackspace Cloud account. `domain |
|                                     |             |enforcement                            |
|                                     |             |<PUT_updateMultiFactorDomain_v2.0_RAX- |
|                                     |             |AUTH_domains__domainId__multi-         |
|                                     |             |factor_.html>`__ domain-level          |
|                                     |             |enforcement is configured as           |
|                                     |             |``Optional``. * ``OPTIONAL.`` The user |
|                                     |             |has the option to authenticate using   |
|                                     |             |multi-factor authentication. *         |
|                                     |             |``DEFAULT.`` The user multi-factor     |
|                                     |             |authentication requirements are        |
|                                     |             |determined by the domain-level         |
|                                     |             |enforcement setting for multi-factor   |
|                                     |             |authentication.                        |
+-------------------------------------+-------------+---------------------------------------+
|unlock                               |Boolean      |A Boolean value that indicates the     |
|                                     |*(Optional)* |lock status on a user account that is  |
|                                     |             |enabled for multi-factor               |
|                                     |             |authentication. To unlock an account,  |
|                                     |             |specify ``unlock=true`` in the Unlock  |
|                                     |             |operation request. .This attribute     |
|                                     |             |cannot be used to lock an account. If  |
|                                     |             |you submit the request with            |
|                                     |             |``unlock=false``, the operation does   |
|                                     |             |not make any changes to the account.   |
+-------------------------------------+-------------+---------------------------------------+





**Example Enable account for multi-factor authentication: XML request header**


.. code::

   PUT /v2.0/users/e0fb2b4ddb594819b697d0048614c117/RAX-AUTH/multi-factor HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/xml
   X-Auth-Token: ab502872c7cc415483c945bcfc77322c
   Content-type: application/xml





**Example Enable account for multi-factor authentication: XML request**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <multiFactor 
        enabled="true"
        xmlns:RAX-AUTH="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
        xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
        xmlns:atom="http://www.w3.org/2005/Atom" 
        xmlns:identity="http://docs.openstack.org/identity/api/v2.0"/>





**Example Enable multi-factor authentication on account: JSON request header**


.. code::

   PUT /v2.0/users/e0fb2b4ddb594819b697d0048614c117/RAX-AUTH/multi-factor HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/xml
   X-Auth-Token: ab502872c7cc415483c945bcfc77322c
   Content-type: application/xml





**Example Enable multi-factor authentication on account: JSON request**


.. code::

   {
       "RAX-AUTH:multiFactor": {
           "enabled": true
       }
   }





**Example Disable multi-factor authentication on account: XML request header**


.. code::

   PUT /v2.0/users/e0fb2b4ddb594819b697d0048614c117/RAX-AUTH/multi-factor HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/xml
   X-Auth-Token: ab502872c7cc415483c945bcfc77322c
   Content-type: application/xml





**Example Disable multi-factor authentication on account: XML request**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <multiFactor 
        enabled="false"
        xmlns:RAX-AUTH="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
        xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
        xmlns:atom="http://www.w3.org/2005/Atom" 
        xmlns:identity="http://docs.openstack.org/identity/api/v2.0"/>





**Example Disable multi-factor authentication on account: JSON request header**


.. code::

   PUT /v2.0/users/e0fb2b4ddb594819b697d0048614c117/RAX-AUTH/multi-factor HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/xml
   X-Auth-Token: ab502872c7cc415483c945bcfc77322c
   Content-type: application/xml





**Example Disable multi-factor authentication on account: JSON request**


.. code::

   {
       "RAX-AUTH:multiFactor": {
           "enabled": false
       }
   }





**Example Unlock account: XML request**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <multiFactor 
        unlock="true"
        xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
        xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
        xmlns:atom="http://www.w3.org/2005/Atom" 
        xmlns:identity="http://docs.openstack.org/identity/api/v2.0"/>





**Example Unlock account: JSON request**


.. code::

   {
       "RAX-AUTH:multiFactor": {
           "unlock": true
       }
   }


This operation does not accept a response body.




**Example Update user level enforcement for multi-factor authentication: XML request**


.. code::

   <multiFactor
       userMultiFactorEnforcementLevel="OPTIONAL"
       xmlns:RAX-AUTH="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
       xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
       xmlns:atom="http://www.w3.org/2005/Atom"
       xmlns:identity="http://docs.openstack.org/identity/api/v2.0"/>
   </multiFactor>
   





**Example Update user level enforcement for multi-factor authentication: JSON request**


.. code::

   {
       "RAX-AUTH:multiFactor": {
           "userMultiFactorEnforcementLevel": "OPTIONAL",
       }
   }





Response
""""""""""""""""






This operation does not return a response body.




