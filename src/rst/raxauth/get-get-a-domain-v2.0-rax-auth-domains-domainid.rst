
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-get-a-domain-v2.0-rax-auth-domains-domainid:

Get a domain
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v2.0/RAX-AUTH/domains/{domainId}

Retrieves a domain. 

.. note::
   This API operation is implemented through the `RAX-AUTH extension <Extensions-d1e688.html>`__ to the core Identity API. 
   
   



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |The request succeeded.   |
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




This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|X-Auth-Token              |String *(Required)*      |A valid authentication   |
|                          |                         |token                    |
+--------------------------+-------------------------+-------------------------+
|{domainId}                |String *(Required)*      |A domain ID.             |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




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
""""""""""""""""





This table shows the body parameters for the response:

+----------------------------------+---------------------+---------------------+
|Name                              |Type                 |Description          |
+==================================+=====================+=====================+
|RAX-AUTH:domain                   |Object *(Required)*  |An object that       |
|                                  |                     |contains the domain  |
|                                  |                     |configuration        |
|                                  |                     |attribute settings.  |
+----------------------------------+---------------------+---------------------+
|id                                |String *(Required)*  |The unique id for    |
|                                  |                     |the domain.          |
+----------------------------------+---------------------+---------------------+
|RAX-AUTH:domain                   |Object *(Required)*  |An object that       |
|                                  |                     |contains the domain  |
|                                  |                     |configuration        |
|                                  |                     |attribute settings.  |
+----------------------------------+---------------------+---------------------+
|enabled                           |Boolean *(Optional)* |Indicates whether    |
|                                  |                     |the domain is        |
|                                  |                     |enabled.             |
+----------------------------------+---------------------+---------------------+
|rax-auth:description              |String *(Optional)*  |The domain           |
|                                  |                     |description.         |
+----------------------------------+---------------------+---------------------+
|name                              |String *(Optional)*  |The domain name.     |
+----------------------------------+---------------------+---------------------+
|domainMultiFactorEnforcementLevel |String *(Optional)*  |If present, this     |
|                                  |                     |extended attribute   |
|                                  |                     |specifies the multi- |
|                                  |                     |factor               |
|                                  |                     |authentication       |
|                                  |                     |enforcement policy   |
|                                  |                     |that applies to      |
|                                  |                     |accounts within the  |
|                                  |                     |specified domain. *  |
|                                  |                     |``REQUIRED`` Users   |
|                                  |                     |within the domain    |
|                                  |                     |must use multi-      |
|                                  |                     |factor               |
|                                  |                     |authentication to    |
|                                  |                     |access their         |
|                                  |                     |account. *           |
|                                  |                     |``OPTIONAL`` Users   |
|                                  |                     |have the option to   |
|                                  |                     |authenticate using   |
|                                  |                     |multi-factor         |
|                                  |                     |authentication.      |
+----------------------------------+---------------------+---------------------+







**Example Get a domain: XML response**


.. code::

   HTTP/1.1 200 OK
   Content-Type: application/xml
   


.. code::

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <rax-auth:domain 
        xmlns:atom="http://www.w3.org/2005/Atom" 
        xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0" 
        xmlns="http://docs.openstack.org/identity/api/v2.0" 
        xmlns:ns4="http://docs.rackspace.com/identity/api/ext/RAX-KSGRP/v1.0" 
        xmlns:rax-ksqa="http://docs.rackspace.com/identity/api/ext/RAX-KSQA/v1.0" 
        xmlns:os-ksadm="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0" 
        xmlns:rax-kskey="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0" 
        xmlns:os-ksec2="http://docs.openstack.org/identity/api/ext/OS-KSEC2/v1.0" id="123456" enabled="true" domainMultiFactorEnforcementLevel="OPTIONAL"></rax-auth:domain>





**Example Get a domain: JSON response**


.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   


.. code::

   {
     "RAX-AUTH:domain": {
       "id": "9883948",
       "enabled": true,
       "description": "A very good customer",
       "name": "GCorp",
       "domainMultiFactorEnforcementLevel": "OPTIONAL"
     }
   }




