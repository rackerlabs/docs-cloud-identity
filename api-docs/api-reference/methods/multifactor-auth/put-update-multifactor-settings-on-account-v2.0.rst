.. _update-multifactor-settings-on-account-v2.0:

Update multi-factor authentication settings on account
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.. code::

    PUT /v2.0/users/{userId}/RAX-AUTH/multi-factor

Use this operation to update the multi-factor authentication settings for
the specified account.

You can only use this operation on accounts that have been
:ref:`set up for multi-factor authentication <multifactor-authenication-ovw>`.

You can use the ``userMultiFactorEnforcementLevel`` parameter to override the
:ref:`multi-factor domain enforcement setting
<update-domain-enforcement-settings-v2.0>`
on an account.  Note that this feature is available only through the API. You
cannot override domain enforcement settings from the Rackspace Cloud Control
Panel.

.. note::

 - Customers need a support ticket if they want to update a user's MFA
   enforcement setting when the domain MFA enforcement setting is
   ``RACKSPACE_MANDATED``.


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
|403                       |Forbidden                |Cannot update user       |
|                          |                         |enforcement level when   |
|                          |                         |domain enforcement level |
|                          |                         |set as                   |
|                          |                         |``RACKSPACE_MANDATED``.  |
+--------------------------+-------------------------+-------------------------+
|500                       |Service Fault            |Problem linking phone    |
|                          |                         |with Identity service    |
|                          |                         |multi-factor             |
|                          |                         |authentication service.  |
|                          |                         |Contact the Identity     |
|                          |                         |service                  |
|                          |                         |administrator for help.  |
+--------------------------+-------------------------+-------------------------+


Request
-------

This table shows the header and URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|X-Auth-Token              |Header                   |A valid admin            |
|                          |String *(Required)*      |authentication token.    |
+--------------------------+-------------------------+-------------------------+
|{userId}                  |URI                      |The unique, system-      |
|                          |String *(Required)*      |generated user ID for an |
|                          |                         |account.                 |
+--------------------------+-------------------------+-------------------------+


This table shows the body parameters for the request:

+-----------------------+--------------+------------------------------------------+
|Name                   |Type          |Description                               |
+=======================+==============+==========================================+
|RAX-                   |Object        |A collection of multi-factor              |
|AUTH:multiFactor       |*(Optional)*  |authentication settings.                  |
+-----------------------+--------------+------------------------------------------+
|RAX-AUTH:multiFactor.\ |Boolean       |If an account has been configured for     |
|**enabled**            |*(Optional)*  |multi-factor authentication,              |
|                       |              |this parameter specifies whether the      |
|                       |              |feature is active on the account.         |
|                       |              |account.                                  |
|                       |              |                                          |
|                       |              |Specify ``enabled=true`` to turn on       |
|                       |              |multi-factor authentication.              |
|                       |              |                                          |
|                       |              |Specify ``enabled=false`` to turn it      |
|                       |              |on.                                       |
|                       |              |                                          |
|                       |              |As soon as you enable multi-factor        |
|                       |              |authentication on an account,             |
|                       |              |any existing authentication tokens are    |
|                       |              |are invalidated, and the account user     |
|                       |              |must use multi-factor authentication      |
|                       |              |process to regain access to their         |
|                       |              |account.                                  |
+-----------------------+--------------+------------------------------------------+
|RAX-AUTH:multiFactor.\ |Boolean       |A Boolean value that indicates the        |
|**unlock**             |*(Optional)*  |lock status on a user account that is     |
|                       |              |enabled for multi-factor                  |
|                       |              |authentication. To unlock an account,     |
|                       |              |specify ``unlock=true`` in the Unlock     |
|                       |              |operation request. .This attribute        |
|                       |              |cannot be used to lock an account. If     |
|                       |              |you submit the request with               |
|                       |              |``unlock=false``, the operation does      |
|                       |              |not make any changes to the account.      |
+-----------------------+--------------+------------------------------------------+
|RAX-AUTH:multiFactor.\ |String        |Specifies the user enforcement level      |
|**userMultiFactor\     |*(Optional)*  |for multi-factor authentication.          |
|EnforcementLevel**     |              |                                          |
|                       |              |``REQUIRED`` The user must use multi-     |
|                       |              |factor authentication to log in to        |
|                       |              |their Rackspace Cloud account even if     |
|                       |              |the :ref:`domain enforcement level        |
|                       |              |<update-domain-enforcement-settings-v2.0>`|
|                       |              |is configured as optional.                |
|                       |              |                                          |
|                       |              |``OPTIONAL.`` The user has the option     |
|                       |              |has the option to authenticate using      |
|                       |              |multi-factor authentication even if the   |
|                       |              |the :ref:`domain enforcement level        |
|                       |              |<update-domain-enforcement-settings-v2.0>`|
|                       |              |is configured as required.                |
|                       |              |                                          |
|                       |              |``DEFAULT.`` The user multi-factor        |
|                       |              |authentication requirements are           |
|                       |              |determined by the domain-level            |
|                       |              |authentication.                           |
+-----------------------+--------------+------------------------------------------+


**Example: Enable account for multi-factor authentication HTTP request header: XML**


.. code::

   PUT /v2.0/users/e0fb2b4ddb594819b697d0048614c117/RAX-AUTH/multi-factor HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/xml
   X-Auth-Token: ab502872c7cc415483c945bcfc77322c
   Content-type: application/xml


**Example: Enable account for multi-factor authentication: XML request**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <multiFactor
        enabled="true"
        xmlns:RAX-AUTH="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
        xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
        xmlns:atom="http://www.w3.org/2005/Atom"
        xmlns:identity="http://docs.openstack.org/identity/api/v2.0"/>


**Example: Enable account for multi-factor authentication HTTP request header: JSON**


.. code::

   PUT /v2.0/users/e0fb2b4ddb594819b697d0048614c117/RAX-AUTH/multi-factor HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/xml
   X-Auth-Token: ab502872c7cc415483c945bcfc77322c
   Content-type: application/xml


**Example: Enable multi-factor authentication on account request: JSON**


.. code::

   {
       "RAX-AUTH:multiFactor": {
           "enabled": true
       }
   }


**Example: Disable multi-factor authentication on account HTTP request header: XML**


.. code::

   PUT /v2.0/users/e0fb2b4ddb594819b697d0048614c117/RAX-AUTH/multi-factor HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/xml
   X-Auth-Token: ab502872c7cc415483c945bcfc77322c
   Content-type: application/xml


**Example: Disable multi-factor authentication on account request: XML**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <multiFactor
        enabled="false"
        xmlns:RAX-AUTH="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
        xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
        xmlns:atom="http://www.w3.org/2005/Atom"
        xmlns:identity="http://docs.openstack.org/identity/api/v2.0"/>


**Example: Disable multi-factor authentication on account HTTP request header: JSON**


.. code::

   PUT /v2.0/users/e0fb2b4ddb594819b697d0048614c117/RAX-AUTH/multi-factor HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/xml
   X-Auth-Token: ab502872c7cc415483c945bcfc77322c
   Content-type: application/xml


**Example: Disable multi-factor authentication on account request: JSON**


.. code::

   {
       "RAX-AUTH:multiFactor": {
           "enabled": false
       }
   }


**Example: Unlock account request: XML**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <multiFactor
        unlock="true"
        xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
        xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
        xmlns:atom="http://www.w3.org/2005/Atom"
        xmlns:identity="http://docs.openstack.org/identity/api/v2.0"/>


**Example: Unlock account request: JSON**


.. code::

   {
       "RAX-AUTH:multiFactor": {
           "unlock": true
       }
   }


This operation does not accept a response body.


**Example: Update user level enforcement for multi-factor authentication request: XML**


.. code::

   <multiFactor
       userMultiFactorEnforcementLevel="OPTIONAL"
       xmlns:RAX-AUTH="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
       xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
       xmlns:atom="http://www.w3.org/2005/Atom"
       xmlns:identity="http://docs.openstack.org/identity/api/v2.0"/>
   </multiFactor>


**Example: Update user level enforcement request: JSON**


.. code::

   {
       "RAX-AUTH:multiFactor": {
           "userMultiFactorEnforcementLevel": "OPTIONAL",
       }
   }


Response
--------
This operation does not return a response body.
