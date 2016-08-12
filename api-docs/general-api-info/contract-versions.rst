.. _contract-versions:

================
Contract version
================

The contract version denotes the data model and behavior that the API
supports. This API documentation provides information about |product name|
contract version ``v2``. The requested contract
version is included in all request URLs. Different API contract versions
might be available at any given time and are not guaranteed to be
compatible with one another.

The URI scheme for API contracts supports the following development
practices:

-  New features and functionality that do not break API compatibility
   are introduced in the current version of the API as
   :ref:`extensions <extensions-ovw>`. The URI version stays the
   same. For example, the Identity service is developing the RAX-AUTH
   extension to develop new services and resources to support the
   Rackspace implementation of OpenStack Keystone v2.0.

-  Service providers must change the API contract version anytime they
   introduce or deprecate features or functionality that make the API
   incompatible with previously released versions. When the version
   changes, the target version in the URI is updated, from v2.0 to v3.0
   for example.

-  When new API versions are released, older versions are
   ``DEPRECATED``. Because a service endpoint can host multiple API
   versions, service providers can work with developers and partners to
   ensure adequate time to migrate to the new version before removing
   the deprecated version from service.

You can use the :ref:`Version <version-operations>` API operations to get
more detailed information about the |apiservice| contract version.
