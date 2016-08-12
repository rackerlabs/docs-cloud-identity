.. _get-get-extension-details-v2.0-extensions-alias:

Get extension details
~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /v2.0/extensions/{alias}

This operation returns detailed information about the specified extension.

Get information about a specific extension by looking up the unique alias.

If an extension is not available, the GET extensions operation returns a
``404`` error message. For a list of aliases, see
:ref:`Extensions <extensions-ovw>`.


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
-------
This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{alias}                   |String                   |The extension name.      |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.


Response
--------

**Example: Get extension details: JSON response**


.. code::

   {
     "extension": {
       "name": "User Metadata Extension",
       "namespace": "http://docs.rackspacecloud.com/identity/api/ext/meta/v2.0",
       "alias": "RS-META",
       "updated": "2011-01-12T11:22:33-06:00",
       "description": "Allows associating arbritrary metadata with a user.",
       "links": [
         {
           "rel": "describedby",
           "type": "application/pdf",
           "href": "http://docs.rackspacecloud.com/identity/api/ext/identity-meta-20111201.pdf"
         }, {
           "rel": "describedby",
           "type": "application/vnd.sun.wadl+xml",
           "href": "http://docs.rackspacecloud.com/identity/api/ext/identity-cbs.wadl"
         }
       ]
     }
   }


**Example: Get extension details: XML response**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>

   <extension xmlns="http://docs.openstack.org/common/api/v1.0"
              xmlns:atom="http://www.w3.org/2005/Atom"
              name="User Metadata Extension"
              namespace="http://docs.rackspacecloud.com/identity/api/ext/meta/v2.0"
              alias="RS-META"
              updated="2011-01-12T11:22:33-06:00">

       <description>
           Allows associating arbritrary metadata with a user.
       </description>

       <atom:link rel="describedby"
                  type="application/pdf"
                  href="http://docs.rackspacecloud.com/identity/api/ext/identity-meta-20111201.pdf"/>
       <atom:link rel="describedby"
                  type="application/vnd.sun.wadl+xml"
                  href="http://docs.rackspacecloud.com/identity/api/ext/identity-meta.wadl"/>

   </extension>
