.. _get-list-extensions-v2.0-extensions:

List extensions
~~~~~~~~~~~~~~~

.. code::

    GET //v2.0/extensions

This operations lists the Identity API extensions that are available in the
Rackspace Identity service. For more information, see the
:ref:`Extensions <extensions-ovw>` section of the Rackspace Identity
Developer Guide.

Applications can programmatically determine which extensions are available by
issuing a GET on the ``/extensions`` URI.

This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |                         |Moves to the next item   |
|                          |                         |in the list. `           |
|                          |                         |<None>`__Moves to the    |
|                          |                         |previous item in the     |
|                          |                         |list. ` <None>`__        |
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
This operation does not accept a request body.




Response
--------

**Example: List Extensions response: JSON**


.. code::

   {
       "extensions":[{
               "name":"Reset Password Extension",
               "namespace":"http://docs.rackspacecloud.com/identity/api/ext/rpe/v2.0",
               "alias":"RS-RPE",
               "updated":"2011-01-22T13:25:27-06:00",
               "description":"Adds the capability to reset a user's password. The user is emailed when the password has been reset.",
               "links":[{
                       "rel":"describedby",
                       "type":"application/pdf",
                       "href":"http://docs.rackspacecloud.com/identity/api/ext/identity-rpe-20111111.pdf"
                   },
                   {
                       "rel":"describedby",
                       "type":"application/vnd.sun.wadl+xml",
                       "href":"http://docs.rackspacecloud.com/identity/api/ext/identity-rpe.wadl"
                   }
               ]
           },
           {
               "name":"User Metadata Extension",
               "namespace":"http://docs.rackspacecloud.com/identity/api/ext/meta/v2.0",
               "alias":"RS-META",
               "updated":"2011-01-12T11:22:33-06:00",
               "description":"Allows associating arbritrary metadata with a user.",
               "links":[{
                       "rel":"describedby",
                       "type":"application/pdf",
                       "href":"http://docs.rackspacecloud.com/identity/api/ext/identity-meta-20111201.pdf"
                   },
                   {
                       "rel":"describedby",
                       "type":"application/vnd.sun.wadl+xml",
                       "href":"http://docs.rackspacecloud.com/identity/api/ext/identity-meta.wadl"
                   }
               ]
           }
       ],
       "extensions_links":[]
   }





**Example: List Extensions response: XML**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>

   <extensions xmlns="http://docs.openstack.org/common/api/v1.0"
               xmlns:atom="http://www.w3.org/2005/Atom">
       <extension
           name="Reset Password Extension"
           namespace="http://docs.rackspacecloud.com/identity/api/ext/rpe/v1.0"
           alias="RS-RPE"
           updated="2011-01-22T13:25:27-06:00">

           <description>
               Adds the capability to reset a user's password.  The user is
               emailed when the password has been reset.
           </description>

           <atom:link rel="describedby"
                      type="application/pdf"
                      href="http://docs.rackspacecloud.com/identity/api/ext/identity-rpe-20111111.pdf"/>
           <atom:link rel="describedby"
                      type="application/vnd.sun.wadl+xml"
                      href="http://docs.rackspacecloud.com/identity/api/ext/identity-rpe.wadl"/>
       </extension>
       <extension
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
   </extensions>
