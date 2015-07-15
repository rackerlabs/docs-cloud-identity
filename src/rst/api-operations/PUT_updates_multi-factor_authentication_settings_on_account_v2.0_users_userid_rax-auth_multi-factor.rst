=============================================================================
Updates Multi-Factor Authentication Settings On Account -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Updates Multi-Factor Authentication Settings On Account
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <PUT_updates_multi-factor_authentication_settings_on_account_v2.0_users_userid_rax-auth_multi-factor.rst#request>`__
`Response <PUT_updates_multi-factor_authentication_settings_on_account_v2.0_users_userid_rax-auth_multi-factor.rst#response>`__

.. code-block:: javascript

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
^^^^^^^^^^^^^^^^^

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{userId}                  |string                   |The unique, system-      |
|                          |                         |generated user ID for an |
|                          |                         |account.                 |
+--------------------------+-------------------------+-------------------------+
|X-Auth-Token              |string *(Required)*      |A valid authentication   |
|                          |                         |token.                   |
+--------------------------+-------------------------+-------------------------+





This table shows the body parameters for the request:

+-------------------------------------+-------------+---------------------------------------+
|Name                                 |Type         |Description                            |
+=====================================+=============+=======================================+
|enabled                              |xsd:Boolean  |A Boolean value that indicates whether |
|                                     |*(Required)* |the account is enabled for multi-      |
|                                     |             |factor authentication. Specify         |
|                                     |             |``enabled=true`` to add support for    |
|                                     |             |multi-factor authentication;           |
|                                     |             |``enabled=false`` to disable it. When  |
|                                     |             |you enable multi-factor authentication,|
+-------------------------------------+-------------+---------------------------------------+
|RAX-                                 |xsd:string   |Specifies the user enforcement level   |
|AUTH:userMultiFactorEnforcementLevel |*(Required)* |for multi-factor authentication:       |
|                                     |             |``REQUIRED`` The user must use multi-  |
|                                     |             |factor authentication to log in to     |
|                                     |             |their Rackspace Cloud account. `domain |
|                                     |             |enforcement                            |
|                                     |             |<PUT_updateMultiFactorDomain_v2.0_RAX- |
|                                     |             |AUTH_domains__domainId__multi-         |
|                                     |             |factor_.html>`__ domain-level          |
|                                     |             |enforcement is configured as           |
|                                     |             |``Optional``. ``OPTIONAL.`` The user   |
|                                     |             |has the option to authenticate using   |
|                                     |             |multi-factor authentication.           |
|                                     |             |``DEFAULT.`` The user multi-factor     |
|                                     |             |authentication requirements are        |
|                                     |             |determined by the domain-level         |
|                                     |             |enforcement setting for multi-factor   |
|                                     |             |authentication.                        |
+-------------------------------------+-------------+---------------------------------------+
|unlock                               |xsd:Boolean  |A Boolean value that indicates the     |
|                                     |*(Required)* |lock status on a user account that is  |
|                                     |             |enabled for multi-factor               |
|                                     |             |authentication. To unlock an account,  |
|                                     |             |specify ``unlock=true`` in the Unlock  |
|                                     |             |operation request. .This attribute     |
|                                     |             |cannot be used to lock an account. If  |
|                                     |             |you submit the request with            |
|                                     |             |``unlock=false``, the operation does   |
|                                     |             |not make any changes to the account.   |
+-------------------------------------+-------------+---------------------------------------+





**Example Enable account for multi-factor authentication: XML request**


.. code::

    PUT /v2.0/users/e0fb2b4ddb594819b697d0048614c117/RAX-AUTH/multi-factor HTTP/1.1
    Host: identity.api.rackspacecloud.com
    Accept: application/json
    X-Auth-Token: ab502872c7cc415483c945bcfc77322c
    Content-type: application/json


**Example Enable multi-factor authentication on account: JSON request**


.. code::

    PUT /v2.0/users/e0fb2b4ddb594819b697d0048614c117/RAX-AUTH/multi-factor HTTP/1.1
    Host: identity.api.rackspacecloud.com
    Accept: application/xml
    X-Auth-Token: ab502872c7cc415483c945bcfc77322c
    Content-type: application/xml


**Example Disable multi-factor authentication on account: XML request**


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
^^^^^^^^^^^^^^^^^^




