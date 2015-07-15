=============================================================================
Get A Domain -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Get A Domain
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_get_a_domain_v2.0_rax-auth_domains_domainid_.rst#request>`__
`Response <GET_get_a_domain_v2.0_rax-auth_domains_domainid_.rst#response>`__

.. code-block:: javascript

    GET /v2.0/RAX-AUTH/domains/{domainId}

Retrieves a domain.

This API operation is implemented through the `RAX-AUTH extension <Extensions-d1e688.html>`__ to the core Identity API.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |The request succeeded.   |
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

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|X-Auth-Token              |string *(Required)*      |A valid authentication   |
|                          |                         |token                    |
+--------------------------+-------------------------+-------------------------+
|{domainId}                |string *(Required)*      |A domain ID.             |
+--------------------------+-------------------------+-------------------------+








**Example Get a domain: XML request**


.. code::

    GET /v2.0/RAX-AUTH/domain/123456 HTTP/1.1
    Host: identity.api.rackspacecloud.com
    Accept: application/xml
    Content-type: application/xml
    X-Auth-Token: c6f56a1d89274da4b14c1de36c412345


**Example Get a domain: JSON request**


.. code::

    GET /v2.0/RAX-AUTH/domain/123456 HTTP/1.1
    Host: identity.api.rackspacecloud.com
    Accept: application/json
    Content-type: application/json
    X-Auth-Token: c6f56a1d89274da4b14c1de36c412345


Response
^^^^^^^^^^^^^^^^^^


This table shows the body parameters for the response:

+----------------------------------+---------------------+---------------------+
|Name                              |Type                 |Description          |
+==================================+=====================+=====================+
|RAX-AUTH:domain                   |object *(Required)*  |An object that       |
|                                  |                     |contains the domain  |
|                                  |                     |configuration        |
|                                  |                     |attribute settings.  |
+----------------------------------+---------------------+---------------------+
|id                                |xsd:string           |The unique id for    |
|                                  |*(Required)*         |the domain.          |
+----------------------------------+---------------------+---------------------+
|RAX-AUTH:domain                   |object *(Required)*  |An object that       |
|                                  |                     |contains the domain  |
|                                  |                     |configuration        |
|                                  |                     |attribute settings.  |
+----------------------------------+---------------------+---------------------+
|enabled                           |xsd:Boolean          |Indicates whether    |
|                                  |*(Required)*         |the domain is        |
|                                  |                     |enabled.             |
+----------------------------------+---------------------+---------------------+
|rax-auth:description              |xsd:string           |The domain           |
|                                  |*(Required)*         |description.         |
+----------------------------------+---------------------+---------------------+
|name                              |xsd:string           |The domain name.     |
|                                  |*(Required)*         |                     |
+----------------------------------+---------------------+---------------------+
|domainMultiFactorEnforcementLevel |string *(Required)*  |If present, this     |
|                                  |                     |extended attribute   |
|                                  |                     |specifies the multi- |
|                                  |                     |factor               |
|                                  |                     |authentication       |
|                                  |                     |enforcement policy   |
|                                  |                     |that applies to      |
|                                  |                     |accounts within the  |
|                                  |                     |specified domain.    |
|                                  |                     |``REQUIRED`` Users   |
|                                  |                     |within the domain    |
|                                  |                     |must use multi-      |
|                                  |                     |factor               |
|                                  |                     |authentication to    |
|                                  |                     |access their         |
|                                  |                     |account.             |
|                                  |                     |``OPTIONAL`` Users   |
|                                  |                     |have the option to   |
|                                  |                     |authenticate using   |
|                                  |                     |multi-factor         |
|                                  |                     |authentication.      |
+----------------------------------+---------------------+---------------------+





**Example Get A Domain: XML request**


.. code::

    HTTP/1.1 200 OK
    Content-Type: application/xml
    


**Example Get A Domain: JSON request**


.. code::

    HTTP/1.1 200 OK
    Content-Type: application/json
    

