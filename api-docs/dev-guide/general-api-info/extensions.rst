.. _extensions-ovw:

API Extensions
~~~~~~~~~~~~~~~~

The authentication service API is extensible, meaning that the API is
structured so that some functions are implemented in the core API and
others are implemented via optional extensions to that core. Extensions
allow Service providers to introduce new features in the API without
changing the contract version and to add custom functionality in their
implementation of the OpenStack architecture.

Every service provider can add extensions to the core API based on
service requirements.

Each extension has two unique identifiers: a namespace and an alias.
These identifiers associate each extension with the vendor that
developed the extension. The identifiers also serve as the labels for
the data types, parameters, actions, headers, states, and resources that
are defined within an extension.

When referencing extended functionality in API requests and responses,
these labels allow you to use entities from multiple extensions in the
same context. The extended resources are available as long as the
extension namespace or alias is provided and the extension is supported
by the API service.

The Identity service supports the following OpenStack and Rackspace
extensions.

-  **OpenStack KSADM**. Supports Create, Read, Update, and Delete (CRUD)
   operations for the following resource types: Users, Tenants, Roles,
   and Services. Requires Administrator privileges.

   -  Alias: OS-KSADM

   -  Namespace:\ ``xmlns:os-ksadm="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"``

-  **OpenStack KSCATALOG Admin**. Supports CRUD operations for Endpoint
   templates and Endpoints. Requires Service administrator privileges.

   -  Alias: OS-KSCATALOG

   -  Namespace:\ ``xmlns:OS-KSCATALOG="http://docs.openstack.org/identity/api/ext/OS-KSCATALOG/v1.0"``

-  **OpenStack KSEC2** . Adds the capability to support EC2 (Amazon
   Elastic Compute) style authentication.

   -  Alias: OS-KSEC2

   -  Namespace:
      ``xmlns:os-ksec2="http://docs.openstack.org/identity/api/ext/OS-KSEC2/v1.0">``

-  **Rackspace API Key Authentication Service**. Adds the API key
   credentials element to support API key authentication for User
   resources.

   -  Alias: RAX-KSKEY

   -  Namespace:\ ``xmlns:rax-kskey="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"``

-  **Rackspace Keystone Group Admin**. Adds administrative support for
   CRUD operations for Group resources.

   -  Alias: RAX-GRPADM

   -  Namespace:\ ``xmlns ="http://docs.rackspace.com/identity/api/ext/RAX-GRPADM/v1.0"``

-  **Rackspace Keystone Group**. Enables group listing for User
   resources.

   -  Alias: RAX-KSGRP

   -  Namespace:\ ``xmlns:ns4="http://docs.rackspace.com/identity/api/ext/RAX-KSGRP/v1.0"``

-  **Rackspace Keystone Extension**. Rackspace implementation that adds
   or extends support for the following resources: Tokens, Users,
   Multifactor (multi-factor authentication), Domains, Impersonation,
   Federation, Regions, Secret Question and Answer, along with Secret
   Question and Answer management.

   -  Alias: RAX-AUTH

   -  Namespace: ``xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"``

-  **Rackspace Keystone Secret Question and Answer**. Supports CRUD
   operations for secret questions and answers for user resources.

   -  Alias: RAX-KSQA

   -  Namespace:\ ``xmlns:rax-ksqa="http://docs.rackspace.com/identity/api/ext/RAX-KSQA/v1.0"``

You can use the Extensions API operations to view and manage the
extensions available with the Identity Service.

.. _extended-resp-actions:

Extended Responses and Actions
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Extensions define new data types, parameters, actions, headers, states,
and resources that are added to the core OpenStack APIs.


.. Important:: 
   During application development, make sure to code for cases where the
   application must ignore response data that contains extension elements
   if the extension is not available. If the application does not support
   an extension, treat all state information as state ``UNKNOWN``.
   Applications must also check whether an extension is available before
   submitting an extended request. Use the :ref:`List extensions <extensions-operations>`
   operation to find out which extensions are available in the application
   environment.

.. _json-req-resp-extensions-json:

JSON requests and responses with extensions
.............................................

In JSON, use the alias to reference extended resources and attributes.
In this Add user API request, you see aliased references to the password
attribute that is provided by the OS-KSADM extension.

 
**Example 3.38. Extended Action: JSON Request**

.. code::  

    {
        "user": {
                "username": "newUser", 
                "email": "newUser@example.com", 
                "enabled": true, 
                "OS-KSADM:password":"Password48"
            }
    }

| 

The API response shows aliases for any elements and attributes that are
provided by extensions. In this example showing a List users response,
the ``defaultRegion`` and ``domainId`` are provided by the RAX-AUTH
extension.

 
**Example 3.39. Extended Server response: JSON**

.. code::  

    {
        "users": [
            {
                "RAX-AUTH:defaultRegion": "DFW",
                "RAX-AUTH:domainId": "660507",
                "email": "testbox@mailtrust.com",
                "enabled": true,
                "id": "000029f0da41496495ea1463c71cc6a5",
                "username": "alicecuser513104"
            },
            {
                "RAX-AUTH:defaultRegion": "IAD",
                "RAX-AUTH:domainId": "6019514",
                "email": "jqsmith112326@thebestemailprovider.com",
                "enabled": true,
                "id": "000064f713e445f78ee8002917207428",
                "username": "jqsmith112326"
            }

        ]
    }

| 

Extended headers are always prefixed with ``X-`` followed by the alias
and a dash: (``X-AUTH-TOKEN``). You must prefix states and parameters
with the extension alias followed by a colon. For example, a user can be
in the ``RAX-AUTH:multiFactorEnabled`` state.


.. _json-req-resp-extensions-xml:

XML requests and responses with extensions
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

In XML, additional elements and attributes are defined in the namespace
for the extension. To use these elements and attributes in an API
request, include the namespace in the API request as shown in this
example.

 
**Example 3.40. Extended Action: XML Request**

.. code::  

    <?xml version="1.0" encoding="UTF-8"?>
    <region enabled="true" isDefault="true" name="DFW"
         xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
         xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
         xmlns:atom="http://www.w3.org/2005/Atom" 
         xmlns:identity="http://docs.openstack.org/identity/api/v2.0"/>

The API response includes the namespaces for core API and extensions
resources available to the API service.

 
**Example 3.41. Extended Identity service: XML Response**

.. code::  

    <?xml version="1.0" encoding="UTF-8"?>
    <users xmlns:atom="http://www.w3.org/2005/Atom" 
        xmlns:rax-auth="http://docs.thebestemailprovider.com/identity/api/ext/RAX-AUTH/v1.0" 
        xmlns="http://docs.openstack.org/identity/api/v2.0" 
        xmlns:ns4="http://docs.thebestemailprovider.com/identity/api/ext/RAX-KSGRP/v1.0" 
        xmlns:rax-ksqa="http://docs.thebestemailprovider.com/identity/api/ext/RAX-KSQA/v1.0" 
        xmlns:os-ksadm="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0" 
        xmlns:rax-kskey="http://docs.thebestemailprovider.com/identity/api/ext/RAX-KSKEY/v1.0" 
        xmlns:os-ksec2="http://docs.openstack.org/identity/api/ext/OS-KSEC2/v1.0">

      <user 
        rax-auth:domainId="660507" 
        rax-auth:defaultRegion="DFW" 
        id="000029f0da41496495ea1463c71cc6a5" 
        username="alicecuser513104" 
        email="testbox@myemailprovider.com" 
        enabled="true"/>
            
      <user 
        rax-auth:domainId="6019514" 
        rax-auth:defaultRegion="IAD" 
        id="000064f713e445f78ee8002917207428" 
        username="jqsmith112326" 
        email="jqsmith112326@thebestemailprovider.com" 
        enabled="true"/>
        
    </users>

| 
