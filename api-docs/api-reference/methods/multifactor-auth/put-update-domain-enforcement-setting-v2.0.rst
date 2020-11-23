.. _update-domain-enforcement-settings-v2.0:

Update domain enforcement setting
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    PUT /v2.0/RAX-AUTH/domains/{domainId}/multi-factor

Updates the domain-level enforcement level for multi-factor authentication.

Identity administrators can set account-wide requirements for multi-factor
authentication  by setting the domain enforcement level. This setting applies
to all user accounts within  the domain specified in the update request. Before
you set the domain enforcement level,  the administrator account must be
configured with multi-factor authentication.

.. note::

 - Administrators can override the domain-level enforcement level for specific
   user accounts by using the
   :ref:`Update multi-factor authentication settings operation
   <update-multifactor-settings-on-account-v2.0>` to set user level enforcement.
 - Customers need a support ticket if they want to update a domain to have the
   ``RACKSPACE_MANDATED`` mfa enforcement policy and also to update a domain's mfa
   enforcement when it is already set to ``RACKSPACE_MANDATED``.


Update domain enforcement settings:json cURL request

.. code::

   $ curl -X -i PUT identity.api.rackspacecloud.com/v2.0/RAX-AUTH/domains/$DOMAIN_ID/multi-factor \
     -d '{"RAX-AUTH:multiFactorDomain": {"domainMultiFactorEnforcementLevel": "OPTIONAL"}}` \
     -H "Content-type: application/json" \
     -H "X-Auth-Token: $ADMIN_AUTH_TOKEN" --verbose | python -m json tool


This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|204                       |No content               |The request succeeded.   |
|                          |                         |The server fulfilled the |
|                          |                         |request but does not     |
|                          |                         |need to return a body.   |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |The request is missing   |
|                          |                         |one or more elements, or |
|                          |                         |the values of some       |
|                          |                         |elements are invalid.    |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |Trying to set up domain- |
|                          |                         |level enforcement        |
|                          |                         |setting on an account    |
|                          |                         |that has not been        |
|                          |                         |configured with multi-   |
|                          |                         |factor authentication.   |
|                          |                         |Set up multi-factor      |
|                          |                         |authentication on        |
|                          |                         |account.                 |
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
|403                       |Forbidden                |You must set up multi-   |
|                          |                         |factor authentication on |
|                          |                         |your account before you  |
|                          |                         |can set multi-factor     |
|                          |                         |domain-level enforcement.|
+--------------------------+-------------------------+-------------------------+
|404                       |Not Found                |The requested resource   |
|                          |                         |was not found.           |
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
|503                       |Service Fault            |Service is not available.|
+--------------------------+-------------------------+-------------------------+


Request
-------

This table shows the body parameters for the request:

+-----------------------+--------------+---------------------------------------+
|Name                   |Type          |Description                            |
+=======================+==============+=======================================+
|RAX-                   |Object        |Specifies the domain enforcement       |
|AUTH:multiFactorDomain |*(Optional)*  |level,                                 |
|                       |              |``domainMultiFactorEnforcementLevel``  |
|                       |              |for multi-factor authentication.       |
|                       |              |Specify either of these values. *      |
|                       |              |``domainMultiFactorEnforcementLevel:   |
|                       |              |"REQUIRED"`` makes multi-factor        |
|                       |              |authentication mandatory for all       |
|                       |              |account users. *                       |
|                       |              |``domainMultiFactorEnforcementLevel:   |
|                       |              |"OPTIONAL"`` Users within the domain   |
|                       |              |can choose whether to use multi-factor |
|                       |              |authentication on their own accounts.  |
|                       |              |``domainMultiFactorEnforcementLevel:   |
|                       |              |"RACKSPACE_MANDATED"`` makes           |
|                       |              |multi-factor authentication mandatory  |
|                       |              |for all account users. *               |
+-----------------------+--------------+---------------------------------------+
|RAX-AUTH:multi\        |String        |The domain enforcement level for       |
|FactorDomain.\         |              |multi-factor authentication. Specify   |
|**domainMultiFactor\   |              |one of the following values:           |
|EnforcementLevel**     |              |                                       |
|                       |              |- ``REQUIRED``                         |
|                       |              |   Authentication is mandatory for all |
|                       |              |   account users within the specified  |
|                       |              |   domain.                             |
|                       |              |                                       |
|                       |              |- ``OPTIONAL``                         |
|                       |              |   Users within the specified domain   |
|                       |              |   can choose whether to use           |
|                       |              |   multi-factor authentication         |
|                       |              |   on their account.                   |
|                       |              |                                       |
|                       |              |- ``RACKSPACE_MANDATED``               |
|                       |              |   Authentication is mandatory for all |
|                       |              |   account users within the specified  |
|                       |              |   domain.                             |
+-----------------------+--------------+---------------------------------------+



**Example: : Update domain settings for multi-factor authentication request: XML**

.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <multiFactorDomain domainMultiFactorEnforcementLevel="REQUIRED"
     xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
     xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
     xmlns:atom="http://www.w3.org/2005/Atom" xmlns:identity="http://docs.openstack.org/identity/api/v2.0"/>


**Example: : Update domain settings for multi-factor authentication request: JSON**

.. code::

   {

       "RAX-AUTH:multiFactorDomain": {
           "domainMultiFactorEnforcementLevel": "REQUIRED"
           }
   }


Response
--------

This operation does not return a response body.
