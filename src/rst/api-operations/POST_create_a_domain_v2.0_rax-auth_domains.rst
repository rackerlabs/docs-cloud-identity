=============================================================================
Create A Domain -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Create A Domain
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <POST_create_a_domain_v2.0_rax-auth_domains.rst#request>`__
`Response <POST_create_a_domain_v2.0_rax-auth_domains.rst#response>`__

.. code-block:: javascript

    POST /v2.0/RAX-AUTH/domains

Creates a domain.

Clients must specify the domain ID in the request body.

Create domain cURL: JSON request in a cURL command$ curl -s $endpoint\2.0\domain \-d '{"RAX-AUTH:domain": {"enabled":true,"id":"myDomainId","name":"newDomain"}}' \-H "Content-type: application/json" \-H "X-Auth-Token: $token \



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|201                       |Created                  |The request has been     |
|                          |                         |fulfilled. The domain    |
|                          |                         |has been created.        |
+--------------------------+-------------------------+-------------------------+
|409                       |Conflict                 |The domain already       |
|                          |                         |exists.                  |
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
|415                       |Bad Media Type           |Bad media type. This may |
|                          |                         |result if the wrong      |
|                          |                         |media type is used in    |
|                          |                         |the API request. Check   |
|                          |                         |the content-type and     |
|                          |                         |accept headers included  |
|                          |                         |in the request.          |
+--------------------------+-------------------------+-------------------------+


Request
^^^^^^^^^^^^^^^^^

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|X-Auth-Token              |string *(Required)*      |A valid authentication   |
|                          |                         |token                    |
+--------------------------+-------------------------+-------------------------+





This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|RAX-AUTH:domain           |object *(Required)*      |Object to specify these  |
|                          |                         |domain configuration     |
|                          |                         |settings: ``id``,        |
|                          |                         |``enabled``, ``name``.   |
+--------------------------+-------------------------+-------------------------+
|id                        |xsd:string *(Required)*  |The unique id for the    |
|                          |                         |domain.                  |
+--------------------------+-------------------------+-------------------------+
|name                      |xsd:string *(Required)*  |The domain name.         |
+--------------------------+-------------------------+-------------------------+
|enabled                   |xsd:Boolean *(Required)* |Set to true to enable    |
|                          |                         |the domain. Otherwise,   |
|                          |                         |set to false.            |
+--------------------------+-------------------------+-------------------------+
|rax-auth:description      |xsd:string *(Required)*  |The domain description.  |
+--------------------------+-------------------------+-------------------------+





**Example Create A Domain: XML request**


.. code::

    POST /v2.0/RAX-AUTH/domains/ HTTP/1.1
    Host: identity.api.rackspacecloud.com
    Accept: application/xml
    Content-type: application/xml
    X-Auth-Token: e681f3fffb9544bc9c46779442d12345


**Example Create A Domain: JSON request**


.. code::

    POST /v2.0/RAX-AUTH/domains/ HTTP/1.1
    Host: identity.api.rackspacecloud.com
    Accept: application/json
    Content-type: application/json
    X-Auth-Token: e681f3fffb9544bc9c46779442d12345


Response
^^^^^^^^^^^^^^^^^^




