.. _get-accessible-domains-for-user-v2.0:

Get accessible domains for user
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /v2.0/users/{userId}/RAX-AUTH/domains

Use the get accessible domains for user operation to retrieve the list of
domains a user has access to.

Request
-------

This table shows the header and URI parameters for the request:

.. csv-table::
    :header: Name, Type, Description
    :widths: 2, 2, 2

    X-Auth-Token, Header String *(Required)*, A valid authentication token.
    {userId}, URI String *(Required)*, A user ID assigned by system when user is added.

Response
--------

The following table shows the body parameters for the retrieve domains
response:

.. csv-table::
    :header: Name, Type, Description
    :widths: 2, 2, 2

    RAX-AUTH:domains, Object *(Required)*, The collection of domains that the authenticated user has permission to view.
    RAX-AUTH:domains.\ **RAX-AUTH:domain**,Object *(Required)*, An object that contains the domain configuration attribute settings.
    RAX-AUTH:domain.\ **id**, String *(Required)*, The unique id for the domain.
    RAX-AUTH:domain.\ **sessionInactivityTimeout**, String *(Required)*, Session inactivity timeout property used across all Rackspace UIs.
    RAX-AUTH:domain.\ **enabled**, Boolean *(Optional)*, Indicates whether the domain is enabled.
    RAX-AUTH:domain.\ **description**, String *(Optional)*, The domain description.
    RAX-AUTH:domain.\ **name**, String *(Optional)*, The domain name.
    RAX-AUTH:domain.\ **rackspaceCustomerNumber**, String *(Optional)*, The Rackspace customer number.
    RAX-AUTH:domain.\ **domainMultiFactorEnforcementLevel**, String *(Optional)*, "If present, this extended attribute specifies the multi-factor authentication enforcement policy that applies to accounts within the specified domain.

    ``REQUIRED`` - Users within the domain must use multi-factor authentication to access their account.

    ``OPTIONAL`` - Users have the option to authenticate using multi-factor authentication."

**Example: Get accessible domains for user: XML response**

.. code::

    < HTTP/1.1 200 OK
    < vary:  Accept, Accept-Encoding, X-Auth-Token
    < Content-Type: application/xml
    < Content-Length: 824

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <rax-auth:domains
        xmlns="http://docs.openstack.org/identity/api/v2.0"
        xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
        xmlns:atom="http://www.w3.org/2005/Atom"
        xmlns:ns4="http://docs.rackspace.com/identity/api/ext/RAX-KSGRP/v1.0"
        xmlns:rax-ksqa="http://docs.rackspace.com/identity/api/ext/RAX-KSQA/v1.0"
        xmlns:os-ksadm="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
        xmlns:rax-kskey="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"
        xmlns:os-ksec2="http://docs.openstack.org/identity/api/ext/OS-KSEC2/v1.0"
        xmlns:ns9="http://docs.openstack.org/identity/api/ext/OS-KSCATALOG/v1.0">
        <rax-auth:domain sessionInactivityTimeout="PT15M" enabled="true" id="123" name="GCorp" rackspaceCustomerNumber="RCN-123-123-123">
            <rax-auth:description>A very good customer</rax-auth:description>
        </rax-auth:domain>
    </rax-auth:domains>

**Example: Get accessible domains for user: JSON response**

.. code::

    < HTTP/1.1 200 OK
    < vary:  Accept, Accept-Encoding, X-Auth-Token
    < Content-Type: application/json
    < Content-Length: 136

    {
        "RAX-AUTH:domains": [
            {
                "enabled": true,
                "id": "123",
                "name": "GCorp",
                "description": "A very good customer",
                "rackspaceCustomerNumber": "RCN-123-123-123"
            }
        ]
    }
