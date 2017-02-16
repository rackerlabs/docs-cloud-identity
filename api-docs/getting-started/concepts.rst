.. _concepts:

==================
|service| concepts
==================

Review the following key concepts to learn how Identity service helps
you login and gain access to Rackspace Cloud services.

.. _user-concept:

User
~~~~~

A user is a digital representation of a person, system, or service that uses
Rackspace Cloud services. Users have credentials and can be assigned tokens.
They can present this information to the Identity service or other Rackspace
Cloud services to confirm identity and verify permission to access the
requested system resources.

Users can also be assigned to a tenant or region so that they inherit a set of
access rights and privileges automatically, based on the tenant or region
configuration.

In the Rackspace Cloud Users are represented as accounts created for assigns a
user type and a default role automatically, based on the Identity service
system configuration. The user type and role determine the resources and
capabilities available to the user.

For more information, see :ref:`Identity Service, admin, and user roles
<auth-roles-svc-adm-usr>`.

.. _authentication-concept:

Authentication
~~~~~~~~~~~~~~

The act of passing in credentials like username and password, confirming an
identity, and returning a token representation of the verified identity.

In the Rackspace Cloud, you authenticate by submitting a **POST tokens** API
request with valid credentials to the Identity service endpoint. Credentials
are typically a user name and API key. However, other types of credentials can
be accepted based on service, tenant, or user account configuration.

In response to valid credentials, the service returns an authentication token
and a service catalog with information about the Rackspace Cloud resources
available for use. In subsequent requests to the Identity service or other
Rackspace Cloud service endpoint, the user includes the authentication token
in the request as proof of identity, rights, and privileges to complete the
requested operation.

.. _credentials-concept:

Credentials
~~~~~~~~~~~

Any kind of information that can be used to verify an identity. For the
Identity service, credentials include these types of information:

-  a matching user name and password

-  a matching user name and API key

-  a unique token issued to you

-  secret question and answer

-  verified cell phone number or email address

-  a multi-factor authentication passcode issued by the Rackspace Cloud
   Identity service


.. _auth-token-concept:

Authentication token
~~~~~~~~~~~~~~~~~~~~

An authentication token is an encrypted string returned by the Identity
service when you submit an authentication request with valid credentials.
Each time that you submit an API request, you include this authentication
token.

Because the token expires after 24 hours, you must generate a new token once
each day. The token stores information about a user's credentials and,
optionally, user identity information, as well as a time stamp and a digital
signature.

If necessary, administrators and users can invalidate a token before it
expires by submitting a Revoke token API request. After a token expires or
becomes invalid, the Identity service returns 404 errors until you
authenticate again.

The Rackspace Cloud Identity service issues authenticated encrypted tokens
(AE). AE tokens are non-persistent tokens that contain encrypted metadata that
supplies all the necessary information to determine whether a token is valid.
For more information, see the :how-to:`Authenticated Encrypted Tokens
<introduction-to-encrypted-authenticated-tokens>` article in the Rackspace
Knowledge Center.

.. _authorization-concept:

Authorization
~~~~~~~~~~~~~

The act of verifying the capability of an authenticated user, system, or
process to perform an action on a set of resources. In the Rackspace Cloud,
the Identity service provides centralized authorization to ensure that clients
have appropriate access to information and information processing capabilities
based on Identity service roles such as system administrator and user
administrator. The Rackspace Cloud also supports Role-based access control
which defines product-specific roles to authorize capabilities at the
service-level.

.. _role-concept:

Role
~~~~

A common security construct for assigning a specific set of access rights and
privileges to a user or group of users. Service administrators can create
named roles, configure the rights and privileges for each role, and manage the
role without updating

Roles can be assigned to users, groups, or tenants automatically based on
organization security policy. An administrator can view, manage, and update
role configuration and assignments as required. Only Identity service service
administrators can create new roles.

Identity service supports two types of roles:

- **Global roles** define access and permissions across all Rackspace
  Cloud services, the administrator or observer roles for example.

- *Product roles* define the functions a user can perform for a
  particular Rackspace Cloud service.

A user with a specific role inherits the rights and privileges associated with
the role. In Rackspace Cloud Identity service, the authentication token issued
to a user includes the list of roles associated with the user. The service
configuration determines how user roles are interpreted. For example, a role
that grants access to certain resources or capabilities within one service can
grant access to completely different resources and capabilities on different
service.

.. _rbac-concept:

Role-based access control (RBAC)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

RBAC is method to restrict service access to only authorized users. RBAC
allows customers to specify who has access to resources and capabilities
within their cloud deployment, based on roles defined by Rackspace. For
example, an administrator can use RBAC to manage access to Cloud Servers as
well as the permissions to complete operations such as adding and deleting
servers after access has been granted.

.. _tenant-concept:

Tenant
~~~~~~

A tenant represents logical groups of users to which resources are assigned.
In the Rackspace Cloud, tenants allow service providers to organize computing
and storage resources without assigning them to user accounts directly. For
example, Virtual machines (Cloud Servers) and containers (Cloud Files) are
assigned to tenants, not to users directly.

Depending on the service provider, a tenant can map to a customer, account,
organization, or project. Identity users can be part of more than one tenant,
and can have different types of roles defined for each tenant that they're a
part of. The Identity service allows you to create and delete tenants, and
also enable and disable them.

Rackspace Cloud has the following two tenant types:

- The Mosso tenant (Mosso account) includes the collection of resources
  commonly associated with services such as Cloud Servers, Cloud Database,
  Cloud Load Balancers.

- The NAST tenant (NAST account) includes the collection of
  resources commonly associated with Cloud Files and Cloud Files CDN.

Typically, a service provider determines how tenants are defined and used. The
Identity service allows service administrators to create, delete, enable, and
disable tenants. Service administrators can also assign users and groups to
one or more tenants. Because each tenant can have its own role configuration,
user can have different roles, or different rights and privileges for the same
role on different tenants.

.. _domain-concept:

Domain
~~~~~~

A domain establishes an administrative boundary for a customer and a space
within the Rackspace Cloud Identity service.

In the Identity service API, the domain resource provides a mechanism to
expose administrative activities directly to system users. Specifically, an
Identity service administrator can create tenants, users, and groups within a
domain and assign roles to users and groups. User administrators that have
domain administrator capabilities can view and manage the domain associated
with their Rackspace Cloud account.

.. _service-concept:

Service
~~~~~~~

A service is a logical name for the internal and external capabilities
provided by a Rackspace Cloud platform or product component. A service
provides one or more endpoints through which users can access resources and
perform operations. Examples of Rackspace Cloud services include Identity,
Servers, Load Balancers, and Files.


.. _endpoint-concept:

Endpoint
~~~~~~~~

A network accessible address, usually described by a URL, where a
service can be accessed.

Various Rackspace Cloud systems can query the Identity service for the service
endpoints required to complete processes and operations. Users must know the
URL for a service endpoint in order to use the service. An API might offer
several regional endpoints for a single API.

The Rackspace Identity service provides one global endpoint:
https://identity.api.rackspacecloud.com. To see supported API versions, browse
to the endpoint URL. To use a specific version of the API, append the version
number to the global endpoint: https://identity.api.rackspacecloud.com/v2.0/.

To get the URLs for other service endpoints, submit an authentication request
with valid credentials to a Identity service endpoint. If authentication is
successful, the Identity service returns an authentication token and a service
catalog with information about available services, including the endpoints to
access each service.

..  note::

    In the Identity service version 1.1 implementation, an endpoint is
    known as a ``baseURL``.

.. _service-catalog-concept:

Service catalog
~~~~~~~~~~~~~~~

Taken as a whole, all the service endpoints defined in Keystone are the
service catalog, defining all services available to OpenStack.

The service catalog is the list of all the service endpoints defined in the
Identity service that represent all services available in the Rackspace Cloud.
When a user authenticates, the authentication response returns a subset of the
service catalog that includes only the services and information that the user
can access. Each service listing includes at least one endpoint URL to access
the service along with other information relevant to using the service such as
region, tenant, and version information. Typically, the service catalog
returned to a System administrator has additional information that might not
be visible to User administrators or Account sub-users.

All the services in the catalog are available as long as you have a valid
authentication token.

.. _federated-identity-management:

Federated identity management
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Federated identity management (FIdM) consists of a set of policies, practices
and protocols that can be used to manage authentication and authorization of
users, processes, and devices across organizations. The goal of identity
federation is to enable users of one domain to securely access data or systems
of another domain seamlessly by passing an authentication token that was
issued by a trusted Identity Provider. Unlike SSO, which allows users to log
in to different domains with the same credentials, federated identity
management allows users to authenticate through a trusted Identity provider
and gain access to any systems that accept identity information from that
provider without providing any additional authentication.
