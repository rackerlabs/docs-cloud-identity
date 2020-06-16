.. _extensions-ovw:

==============
API Extensions
==============

The |apiservice| uses extensions to implement some functionality that is not
available in the core OpenStack Keystone API. Extensions allow Service
providers like Rackspace to introduce new features in the API without changing
the contract version and to add custom functionality in their implementation
of the OpenStack architecture.

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

You can use the :ref:`Extensions API operations <extensions-operations>`
to view and manage the extensions available with the |apiservice| as shown in
the following sections:


.. _extended-resp-actions:

Extended Responses and Actions
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

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
-------------------------------------------

In JSON, use the alias to reference extended resources and attributes.
In this Get user admin API request, you see aliased references to the user
attributes that are provided by the RAX-AUTH extension.

**Example 3.38. Extended Action: cURL Request**

.. code::

      $ curl -X GET $ENDPOINT/v2.0/users/$USER_ID/RAX-AUTH/admins \
             -H "Content-type: application/json" \
             -H "X-Auth-Token: $AUTH_TOKEN"  | python -m json.tool

The API response shows aliases for any elements and attributes that are
provided by extensions. In the following example, the response to the get user
admin request returns the following extended attributes that are supported by
the RAX-AUTH extension: ``defaultRegion``, ``domainId``, and
``multiFactorEnabled``.

**Example: Extended Server HTTP and JSON response**

.. code::

     HTTP/1.1 200 OK
     Server: nginx
     Date: Wed, 10 Aug 2016 20:31:21 GMT
     Content-Type: application/json
     Content-Length: 225
     Connection: keep-alive
     Vary: Accept, Accept-Encoding, X-Auth-Token
     X-NewRelic-App-Data: PxQCWVFVDwQTVVRTBAQAUlATGhE1AwE2QgNWEVlbQFtcC2VOYwRAFjNTVTIDEU5aUwE9TUJCUhQXbRlIFxUGEHkGRT4XanVqHiRsNXk9HAMAW14PFUMQdHUwSEAbARlWSAEYAlRUVloAWg5OFQkYEABWClAGWFFRU1RUWF8FWlISSAcDW0JSOw==
     x-trans-id: eyJyZXF1ZXN0SWQiOiI1N2FmZDI4Zi0zNzViLTQ5MzYtYmI5ZS0yMDUxMGJmNTA0YzYiLCJvcmlnaW4iOm51bGx9
     Front-End-Https: on

.. code::

     {
         "users": [
             {
                "RAX-AUTH:defaultRegion": "IAD",
                "RAX-AUTH:domainId": "123456",
                "RAX-AUTH:multiFactorEnabled": false,
                "email": "user@email.com",
                "enabled": true,
                "id": "10d2c2d0f3b644b9abea0d9564321234",
                "username": ""
             }
        ]
     }

Extended headers are always prefixed with ``X-`` followed by the alias
and a dash: (``X-AUTH-TOKEN``). You must prefix states and parameters
with the extension alias followed by a colon. For example, a user can be
in the ``RAX-AUTH:multiFactorEnabled`` state.


.. _xml-req-resp-extensions-xml:

XML requests and responses with extensions
------------------------------------------

In XML, additional elements and attributes are defined in the namespace
for the extension. To use these elements and attributes in an API
request, include the namespace in the API request as shown in this
example.

**Example: Extended Action: cURL Request**

.. code::

      $ curl -X GET $ENDPOINT/v2.0/users/$USER_ID/RAX-AUTH/admins.xml
             -H "Content-type: application/xml"
             -H "X-Auth-Token: $AUTH_TOKEN"  | xml

The API response includes the namespaces for core API and extensions
resources available to the API service.

**Example: Extended Identity service: HTTP and XML response**

.. code::

     <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
       <users
          xmlns="http://docs.openstack.org/identity/api/v2.0"
          xmlns:os-ksec2="http://docs.openstack.org/identity/api/ext/OS-KSEC2/v1.0"
          xmlns:rax-kskey="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"
          xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
          xmlns:rax-ksqa="http://docs.rackspace.com/identity/api/ext/RAX-KSQA/v1.0"
          xmlns:atom="http://www.w3.org/2005/Atom"
          xmlns:ns7="http://docs.rackspace.com/identity/api/ext/RAX-KSGRP/v1.0"
          xmlns:os-ksadm="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0">
          <user
               enabled="true"
               email="margaret.eker@rackspace.com"
               username="maeker123"
               id="10d2c2d0f3b644b9abea0d9fe80669e4"
               rax-auth:multiFactorEnabled="false"
               rax-auth:defaultRegion="IAD"
               rax-auth:domainId="929418"/>
    </users>

