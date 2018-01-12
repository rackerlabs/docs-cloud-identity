.. _identity-provider-operations:

=================
Identity provider
=================

An Identity Provider (IDP) is required in order to federate with Identity.
Services are provided to manage Identity Providers (IDPs) within Identity.

**Access restrictions**

Access to the CRUD Identity Provider Management services using metadata are
controlled via the following roles.

.. csv-table::
   :header: Service, identity:user-admin, identity:user-manage, rcn:admin
   :widths: auto

   CreateIDPs, Yes, Yes, Yes
   UpdateIDPs, Yes, Yes, Yes
   GetIDPs, Yes, Yes, Yes
   ListIDPs, Yes, Yes, Yes
   GetIDPsMetadata, Yes, Yes, Yes
   GetIDPsMappingPolicy, Yes, Yes, Yes
   UpdateIDPsMappingPolicy, Yes, Yes, Yes

.. note::

   - User-admin or User-manage can make requests only when the caller’s domain
     is the same as the specified Identity Provider’s (IDP’s)
     ``approvedDomainId``.
   - A user with the role rcn:admin can make requests only when the caller’s
     domain is within the same RCN as the IDP’s specified ``approvedDomainId``.


Use the following API operations to create, review, update, and delete
Identity Providers.

.. contents::
   :local:
   :depth: 1

.. include:: methods/identity-provider/post-create-identity-provider-with-metadata-v2.0.rst
.. include:: methods/identity-provider/put-update-identity-provider-v2.0.rst
.. include:: methods/identity-provider/put-update-identity-provider-with-metadata-v2.0.rst
.. include:: methods/identity-provider/get-identity-provider-v2.0.rst
.. include:: methods/identity-provider/get-list-identity-providers-v2.0.rst
.. include:: methods/identity-provider/get-identity-provider-metadata-v2.0.rst
.. include:: methods/identity-provider/get-identity-provider-mapping-policy-v2.0.rst
.. include:: methods/identity-provider/put-update-identity-provider-mapping-policy-v2.0.rst
