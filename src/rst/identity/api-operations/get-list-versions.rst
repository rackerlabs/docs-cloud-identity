
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-list-versions:

List versions
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /

Lists information about the API versions supported by the Identity service at the specified API service endpoint.

Use the GET version operation to discover API version information for the Identity service, links to documentation (PDF, HTML, WADL), and supported media types. You can complete this operation from the browser by entering the URL for the Identity API service endpoint: `https://identity.api.rackspacecloud.com <https://identity.api.rackspacecloud.com/v2.0>`__ for example.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |                         |` <None>`__An array that |
|                          |                         |returns the list of API  |
|                          |                         |versions supported by    |
|                          |                         |the Rackspace Cloud      |
|                          |                         |environment at the       |
|                          |                         |specified endpoint.The   |
|                          |                         |``version`` parameter is |
|                          |                         |an array that provides   |
|                          |                         |the API version number   |
|                          |                         |and detailed meta        |
|                          |                         |information regarding    |
|                          |                         |the status of the        |
|                          |                         |current API version. The |
|                          |                         |description includes an  |
|                          |                         |id for the API version,  |
|                          |                         |links to both human      |
|                          |                         |readable and a machine   |
|                          |                         |processable description  |
|                          |                         |of the API service. The  |
|                          |                         |``status`` parameter     |
|                          |                         |describes the current    |
|                          |                         |operational state of the |
|                          |                         |given service version.   |
|                          |                         |Status can be any of the |
|                          |                         |following values: *      |
|                          |                         |ALPHA status describes a |
|                          |                         |new service API. The API |
|                          |                         |contract might be set,   |
|                          |                         |but the API              |
|                          |                         |implementation might not |
|                          |                         |comply with the contract |
|                          |                         |completely. Developers   |
|                          |                         |are encouraged to begin  |
|                          |                         |testing against an ALPHA |
|                          |                         |version to provide       |
|                          |                         |feedback. * BETA status  |
|                          |                         |describes an API version |
|                          |                         |that is a candidate for  |
|                          |                         |the next major release.  |
|                          |                         |BETA versions might      |
|                          |                         |include functionality    |
|                          |                         |not available in the     |
|                          |                         |current version.         |
|                          |                         |Developers are           |
|                          |                         |encouraged to test and   |
|                          |                         |begin the process of     |
|                          |                         |migrating to a BETA      |
|                          |                         |version. Note that a     |
|                          |                         |BETA version is          |
|                          |                         |undergoing testing, it   |
|                          |                         |has not been officially  |
|                          |                         |released, and might not  |
|                          |                         |be stable. * CURRENT     |
|                          |                         |status describes a       |
|                          |                         |stable, tested API       |
|                          |                         |version. Developers are  |
|                          |                         |encouraged to develop    |
|                          |                         |against this version.    |
|                          |                         |The status value for the |
|                          |                         |current released API     |
|                          |                         |version is               |
|                          |                         |always``CURRENT``. *     |
|                          |                         |DEPRECATED describes an  |
|                          |                         |older version of the API |
|                          |                         |that has been replaced   |
|                          |                         |by a newer version.      |
|                          |                         |Application developers   |
|                          |                         |are discouraged from     |
|                          |                         |using or developing      |
|                          |                         |against this version.    |
|                          |                         |Use the latest, current  |
|                          |                         |version of the API       |
|                          |                         |instead.                 |
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
""""""""""""""""








This operation does not accept a request body.




Response
""""""""""""""""





This table shows the body parameters for the response:

+-------------------------------------------+-------------------+--------------+
|Name                                       |Type               |Description   |
+===========================================+===================+==============+
|/capi:version/atom:link[@rel='self']/@href |Anyuri *(Required)*|` <None>`__   |
+-------------------------------------------+-------------------+--------------+
|versions                                   |Versionchoicelist  |An array that |
|                                           |*(Required)*       |returns the   |
|                                           |                   |list of API   |
|                                           |                   |versions      |
|                                           |                   |supported by  |
|                                           |                   |the Rackspace |
|                                           |                   |Cloud         |
|                                           |                   |environment   |
|                                           |                   |at the        |
|                                           |                   |specified     |
|                                           |                   |endpoint.     |
+-------------------------------------------+-------------------+--------------+
|version                                    |Versionchoice      |The           |
|                                           |*(Required)*       |``version``   |
|                                           |                   |parameter is  |
|                                           |                   |an array that |
|                                           |                   |provides the  |
|                                           |                   |API version   |
|                                           |                   |number and    |
|                                           |                   |detailed meta |
|                                           |                   |information   |
|                                           |                   |regarding the |
|                                           |                   |status of the |
|                                           |                   |current API   |
|                                           |                   |version. The  |
|                                           |                   |description   |
|                                           |                   |includes an   |
|                                           |                   |id for the    |
|                                           |                   |API version,  |
|                                           |                   |links to both |
|                                           |                   |human         |
|                                           |                   |readable and  |
|                                           |                   |a machine     |
|                                           |                   |processable   |
|                                           |                   |description   |
|                                           |                   |of the API    |
|                                           |                   |service.      |
+-------------------------------------------+-------------------+--------------+







**Example List versions: JSON response**


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





**Example List versions: XML response**


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




