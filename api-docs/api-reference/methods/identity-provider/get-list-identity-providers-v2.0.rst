.. _get-list-identity-providers-v2.0:

List IDPs
~~~~~~~~~

.. code::

   GET /v2.0/RAX-AUTH/federation/identity-providers

List Identity providers.

.. note::

   - User-admin or User-manage can list only Identity Providers that are
     within the same domain.
   - A user with the role rcn:admin can list only Identity Providers which
     are within the same RCN as the IDP’s specified ``approvedDomainId``.

This table shows the possible response codes for this operation:

.. csv-table::
   :header: Response Code, Name, Description
   :widths: 2, 2, 2

   200, OK, The request has succeeded.
   400, Bad Request, If both the ``approvedTenantId`` and ``approvedDomainId`` query params are provided.
   400, Bad Request, If the idpType param is specified with an unsupported value.
   403, Forbidden, Caller does not have appropriate role.
   403, Forbidden, If more than the maximum number of IDPs would be returned by the search - as specified by configuration property identity.provider.max.search.result.size.

Request
-------

This table shows the header parameters for the request:

.. csv-table::
   :header: Name, Type, Description
   :widths: 2, 2, 2

   X-Auth-Token, String *(Required)*, A valid authentication token.

This table shows the query parameters for the request:

.. csv-table::
   :header: Name, Type, Description
   :widths: 2, 2, 2

   name, String *(Optional)*, Allows searching IDPs by ``name`` specified. This will return a list of max size one.
   issuer, String *(Optional)*, Allows searching IDPs by ``issuer`` specified. This will return a list of max size one.
   idpType, String *(Optional)*, "When specified the resultant list of IDPs will ONLY include IDPs that match the specified type. The allowed values are:

   - ``EXPLICIT`` - Limits results to only those IDPs that were created with an ``approvedDomainIds`` specified

   The ``idpType`` filter can be provided by itself OR combined with ``approvedDomainId`` filter"
   approvedDomainId, String *(Optional)*, "Limits the resultant IDPs to those DOMAIN federated IDPs that can request tokens for the specified domain. This will include those DOMAIN federated IDPs that are GLOBAL IDPs (created with ``approvedDomainGroup`` = ``GLOBAL``)

   The ``approvedDomainId`` and ``idpType`` filters can be used together to limit the result list to non-global domain ids that are explicitly configured for a given domain."
   approvedTenantId, String *(Optional)*, "When specified the resultant list of IDPs will ONLY include IDPs that can receive tokens for the specified tenantId. The service will look up the domainId associated with the specific tenantId to determine which IDPs can received tokens for the given tenantId.

   The ``approvedTenantId`` and ``approvedDomainId`` filters are mutually exclusive. If both are specified, a ``HTTP 400`` response will be returned.

   The ``approvedTenantId`` and ``idpType`` filters can be used together to limit the result list to non-global domain ids that are explicitly configured for a given domain."

Response
--------

**Example:  List IDPs: XML response**

.. code::

   < HTTP/1.1 200 OK
   < vary:  Accept, Accept-Encoding, X-Auth-Token
   < Content-Type: application/xml

    <?xml version="1.0" encoding="UTF-8"?>
    <identityProviders xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
                      xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
                      xmlns:atom="http://www.w3.org/2005/Atom" xmlns:identity="http://docs.openstack.org/identity/api/v2.0">
        <identityProvider id="asdfqwerr" name="name1" issuer="https://my.issuer.com" authenticationUrl="https://my.login.com" description="A description" federationType="DOMAIN">
            <approvedDomainIds>
                <approvedDomainId>12345</approvedDomainId>
            </approvedDomainIds>
        </identityProvider>
        <identityProvider id="ty656" name="name2" issuer="https://my.issuer.com" authenticationUrl="https://my.login.com" description="A description" federationType="DOMAIN" approvedDomainGroup="GLOBAL" />
        <identityProvider id="jiyougfhjhrt" name="name3" issuer="https://my.issuer2.com" authenticationUrl="https://my.login.com" description="Another description" federationType="RACKER" />
    </identityProviders>

**Example:  List IDPs: JSON response**

.. code::

   < HTTP/1.1 200 OK
   < vary:  Accept, Accept-Encoding, X-Auth-Token
   < Content-Type: application/json

    {
      "RAX-AUTH:identityProviders": [
        {
          "id": "asdfqwerr",
          "name": "name1",
          "issuer": "https://my.issuer.com",
          "description": "A description",
          "federationType": "DOMAIN",
          "authenticationUrl": "https://my.login.com",
          "approvedDomainIds": [
            "12345"
          ]
        },
        {
          "id": "byfghrt",
          "name": "name2",
          "issuer": "https://my.issuer.com",
          "description": "A description",
          "federationType": "DOMAIN",
          "authenticationUrl": "https://my.login.com",
          "approvedDomainGroup": "GLOBAL"
        },
        {
          "id": "jiyougfhjhrt",
          "name": "name3",
          "issuer": "https://my.issuer2.com",
          "description": "Another description",
          "authenticationUrl": "https://my.login.com",
          "federationType": "RACKER"
        }
      ]
    }
