.. _contract-versions:

Contract versions
~~~~~~~~~~~~~~~~~~

The contract version denotes the data model and behavior that the API
supports. The Identity API uses a URI version scheme.

.. Important:: 
    The Rackspace implementation of the OpenStack Keystone Identity Service
    v2.0 does not yet support MIME-type version.

    All client requests to the API must specify the target version
    identifier in the first element of the URI path. For example, v2.0 is
    the target version in this enddpoint URI:

.. code::  

    https://identity.api.rackspacecloud.com/v2.0/

The only access available without the target version are to check for
the GET version API request that returns available API versions
supported at the specified endpoint.

The folloiwng example shows an XML request that uses URI versioning.

 
**Example: Request with URI version scheme**

.. code:: 

    GET /v2.0/tenants HTTP/1.1
    Host: identity.api.rackspacecloud.com
    Accept: application/xml
    X-Auth-Token: eaaafd18-0fed-4b3a-81b4-663c99ec1cbb
    
                
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

You can programmatically determine available API versions by performing
a **GET** on the root URL returned from the authentication system. In
the root URL, the version and everything to the right of it is
truncated. An Atom representation of the version's resources is
supported when issuing a request with the ``Accept`` header containing
``application/atom+xml`` or by adding ``.atom`` to the request URI. This
allows standard Atom clients to track version changes.

 
**Example 3.30. Versions List Request**

.. code:: 

    GET HTTP/1.1
    Host: identity.api.rackspacecloud.com
                

Normal Response Code(s): 200, 203

Error Response Code(s): badRequest (400), identityFault (500),
serviceUnavailable(503)

This operation does not require a request body.

 
**Example 3.31. Versions List Response: XML**

.. code::  

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>

    <versions xmlns="http://docs.openstack.org/common/api/v1.0" xmlns:atom="http://www.w3.org/2005/Atom" xmlns:ns3="http://docs.rackspace.com/core/event">

            <version updated="2011-07-19T22:30:00Z" status="DEPRECATED" id="v1.0">
                    <atom:link href="https://identity.api.rackspacecloud.com/v1.0" rel="self"/>
            </version>

            <version updated="2012-01-19T22:30:00.25Z" status="CURRENT" id="v1.1">
                    <atom:link href="https://identity.api.rackspacecloud.com/v1.1/" rel="self"/>
                    <atom:link href="http://docs.rackspacecloud.com/auth/api/v1.1/auth-client-devguide-latest.pdf" rel="describedby" type="application/pdf"/>
                    <atom:link href="http://docs.rackspacecloud.com/auth/api/v1.1/auth.wadl" rel="describedby" type="application/vnd.sun.wadl+xml"/>
            </version>

            <version updated="2012-01-19T22:30:00.25Z" status="CURRENT" id="v2.0">
                    <atom:link href="https://identity.api.rackspacecloud.com/v2.0/" rel="self"/>
                    <atom:link href="http://docs.rackspacecloud.com/auth/api/v2.0/auth-client-devguide-latest.pdf" rel="describedby" type="application/pdf"/>
                    <atom:link href="http://docs.rackspacecloud.com/auth/api/v2.0/auth.wadl" rel="describedby" type="application/vnd.sun.wadl+xml"/>
            </version>

    </versions>

                

 
**Example 3.32. Versions List Response: Atom**

.. code::  

    <?xml version="1.0" encoding="UTF-8"?>
    <feed xmlns="http://www.w3.org/2005/Atom">
        <title type="text">Available API Versions</title>
        <updated>2010-12-12T18:30:02.25Z</updated>
       <id>http://identity.api.rackspacecloud.com/</id>
        <author><name>Rackspace</name><uri>http://www.rackspace.com/</uri></author>
       <link rel="self" href="http://identity.api.rackspacecloud.com/"/>
        <entry>
           <id>http://identity.api.rackspacecloud.com/v2.0/</id>
           <title type="text">Version v2.0</title>
           <updated>2011-05-27T20:22:02.25Z</updated>
           <link rel="self" href="http://identity.api.rackspacecloud.com/v2.0/"/>
           <content type="text">Version v2.1 CURRENT (2011-05-27T20:22:02.25Z)</content>
        </entry>
        <entry>
           <id>http://identity.api.rackspacecloud.com/v1.1/</id>
           <title type="text">Version v1.1</title>
           <updated>2010-12-12T18:30:02.25Z</updated>
           <link rel="self" href="http://identity.api.rackspacecloud.com/v1.1/"/>
           <content type="text">Version v1.1 CURRENT (2010-12-12T18:30:02.25Z)</content>
        </entry>
        <entry>
           <id>http://identity.api.rackspacecloud.com/v1.0/</id>
           <title type="text">Version v1.0</title>
           <updated>2009-10-09T11:30:00Z</updated>
           <link rel="self" href="http://identity.api.rackspacecloud.com/v1.0/"/>
           <content type="text">Version v1.0 DEPRECATED (2009-10-09T11:30:00Z)</content>
        </entry>
    </feed>

                

 
**Example 3.33. Versions List Response: JSON**

.. code::  

    {
        "versions": {
            "version": [
                {
                    "id": "v1.0",
                    "link": {
                        "href": "https://identity.api.rackspacecloud.com/v1.0",
                        "rel": "self"
                    },
                    "status": "DEPRECATED",
                    "updated": "2011-07-19T22:30:00Z"
                },
                {
                    "id": "v1.1",
                    "link": {
                        "href": "http://docs.rackspacecloud.com/auth/api/v1.1/auth.wadl",
                        "rel": "describedby",
                        "type": "application/vnd.sun.wadl+xml"
                    },
                    "status": "CURRENT",
                    "updated": "2012-01-19T22:30:00.25Z"
                },
                {
                    "id": "v2.0",
                    "link": {
                        "href": "http://docs.rackspacecloud.com/auth/api/v2.0/auth.wadl",
                        "rel": "describedby",
                        "type": "application/vnd.sun.wadl+xml"
                    },
                    "status": "CURRENT",
                    "updated": "2012-01-19T22:30:00.25Z"
                }
            ]
        }
    }

You can obtain additional detailed information about a specific version
by performing a **GET** on the base version URL. For example,
``https://identity.api.rackspacecloud.com/v2.0/`` is a base version URL,
in which ``v2.0`` is the initial version of the API. All version request
URLs end with a trailing slash (/). If the slash is omitted, the server
might respond with a 302 redirection request. You can add format
extensions after the trailing slash. For example,
``https://identity.api.rackspacecloud.com/v2.0/.xml`` includes ``.xml``
as a format extension. Note that this is a special case that does not
hold true for other API requests. In general, requests such as
``/tenants.xml`` and ``/tenants/.xml`` are handled equivalently.

 
**Example 3.34. Version Details Request**

.. code:: 

    GET HTTP/1.1
    Host: identity.api.rackspacecloud.com/v1.0/
                

Normal Response Code(s): 200, 203

Error Response Code(s): badRequest (400), identityFault (500),
serviceUnavailable(503)

This operation does not require a request body.

 
**Example 3.35. Version Details Response: XML**

.. code::  

    <?xml version="1.0" encoding="UTF-8"?>
    <version xmlns="http://docs.openstack.org/common/api/v1.0"
             xmlns:atom="http://www.w3.org/2005/Atom"
             id="v2.0" status="CURRENT" updated="2011-01-21T11:33:21-06:00">

         <media-types>
             <media-type base="application/xml"
                type="application/vnd.openstack.identity+xml;version=2.0"/>
             <media-type base="application/json"
                type="application/vnd.openstack.identity+json;version=2.0"/>
         </media-types>

         <atom:link rel="self"
             href="https://identity.api.rackspacecloud.com/v2.0/"/>

        <atom:link rel="describedby"
                   type="application/pdf"
                   href="http://docs.rackspace.com/auth/api/v2.0/auth-client-devguide-latest.pdf" />

        <atom:link rel="describedby"
                   type="application/vnd.sun.wadl+xml"
                   href="http://docs.rackspacecloud.com/auth/api/v2.0/auth.wadl" />
    </version>

                

 
**Example 3.36. Version Details Response: Atom**

.. code::  

    <?xml version="1.0" encoding="UTF-8"?>
    <feed xmlns="http://www.w3.org/2005/Atom">
      <title type="text">About This Version</title>
      <updated>2011-01-21T11:33:21-06:00</updated>
      <id>https://identity.api.rackspacecloud.com/v2.0/</id>
       <author><name>OpenStack</name><uri>http://www.openstack.org/</uri></author>
       <link rel="self" href="http://identity.api.openstack.org/v2.0/"/>
       <entry>
          <id>http://identity.api.rackspacecloud.com/v2.0/</id>
          <title type="text">Version v2.0</title>
          <updated>2011-01-21T11:33:21-06:00</updated>
         <link rel="self" href="http://identity.api.rackspace.com/v2.0/"/>
          <link rel="describedby" type="application/pdf"
               href="http://docs.rackspace.com/auth/api/v2.0/auth-client-devguide-latest.pdf"/>
          <link rel="describedby" type="application/vnd.sun.wadl+xml"
               href="http://docs.rackspace.com/auth/api/v2.0/auth.wadl"/>
          <content type="text">Version v2.0 CURRENT (2011-01-21T11:33:21-06:00)</content>
       </entry>
    </feed>

                

 
**Example 3.37. Version details response: JSON**

.. code::  

    {
        "version": {
            "id": "v2.0",
            "links": [
                {
                    "href": "https://identity.api.rackspacecloud.com/v2.0",
                    "rel": "self"
                },
                {
                    "href": "http://docs.rackspace.com/auth/api/v2.0/auth-client-devguide-latest.pdf",
                    "rel": "describedby",
                    "type": "application/pdf"
                },
                {
                    "href": "http://docs.rackspacecloud.com/auth/api/v2.0/auth.wadl",
                    "rel": "describedby",
                    "type": "application/vnd.sun.wadl+xml"
                }
            ],
            "media-types": {
                "values": [
                    {
                        "base": "application/xml",
                        "type": "application/vnd.openstack.identity+xml;version=2.0"
                    },
                    {
                        "base": "application/json",
                        "type": "application/vnd.openstack.identity+json;version=2.0"
                    }
                ]
            },
            "status": "CURRENT",
            "updated": "2012-01-21T11:33:21-06:00"
        }
    }

The detailed version response contains pointers to both a human-readable
and a machine-processable description of the API service. The
machine-processable description is written in the Web Application
Description Language (WADL).

..  note:: 
    If there is a discrepancy between the two specifications, the WADL is
    authoritative as it contains the most accurate and up-to-date
    description of the API service.
