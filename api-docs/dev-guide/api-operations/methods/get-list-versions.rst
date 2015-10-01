
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-list-versions:

List versions
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /

This operation returns a list of the available Rackspace Cloud Identity API versions.


This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |The operation completed  |
|                          |                         |successfully.            |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |The request is missing   |
|                          |                         |one or more elements, or |
|                          |                         |the values of some       |
|                          |                         |elements are invalid.    |
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
""""""""""""""""

This operation does not accept a request body.

**Example: List versions: XML request**


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


Response
""""""""""""""""

**Example: List versions: XML response**


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


**Example: List versions: JSON response**


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




