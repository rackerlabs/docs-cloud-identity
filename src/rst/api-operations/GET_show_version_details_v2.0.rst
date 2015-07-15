=============================================================================
Show Version Details -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Show Version Details
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_show_version_details_v2.0.rst#request>`__
`Response <GET_show_version_details_v2.0.rst#response>`__

.. code-block:: javascript

    GET /v2.0

Shows details for the Identity API v2.0.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |The operation completed  |
|                          |                         |successfully.            |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |The request is missing   |
|                          |                         |one or more elements, or |
|                          |                         |the values of            |
|                          |                         |someelements are invalid.|
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
|                          |                         |requested                |
|                          |                         |resource.Submit a        |
|                          |                         |request to your account  |
|                          |                         |administrator to         |
|                          |                         |determine how to gain    |
|                          |                         |access.                  |
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
|404                       |Not Found                |The requested resource   |
|                          |                         |was not found.           |
+--------------------------+-------------------------+-------------------------+


Request
^^^^^^^^^^^^^^^^^









Response
^^^^^^^^^^^^^^^^^^





**Example Show Version Details: JSON request**


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


**Example Show Version Details: XML request**


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

