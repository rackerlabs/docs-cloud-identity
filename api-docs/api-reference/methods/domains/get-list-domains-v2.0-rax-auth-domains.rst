.. _get-list-domains-v2.0:

Retrieve domains
~~~~~~~~~~~~~~~~

.. code::

    GET /v2.0/RAX-AUTH/domains

Lists domains that a customer or process can access with the specified
authentication token.

Use this operation to get a list of domains that the user can access with the
supplied authentication token.  Tokens have access to domains by the token
having access to a tenant that exists in the domain.

.. note::

   This API operation is implemented through the
   :ref:`RAX-AUTH extension <extensions-ovw>` to the core Identity API.


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
-------

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|X-Auth-Token              |String *(Required)*      |A valid authentication   |
|                          |                         |token                    |
+--------------------------+-------------------------+-------------------------+


This operation does not accept a request body.

**Example: List domains HTTP request header: XML**


.. code::

   GET /v2.0/RAX-AUTH/domains/123456 HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/xml
   Content-type: application/xml
   X-Auth-Token: c6f56a1d89274da4b14c1de36c412345



**Example: List domains HTTP request header: JSON**


.. code::

   GET /v2.0/RAX-AUTH/domains HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/json
   Content-type: application/json
   X-Auth-Token: c6f56a1d89274da4b14c1de36c412345





Response
--------


This table shows the body parameters for the response:

+-------------------------------------+---------------------+---------------------+
|Name                                 |Type                 |Description          |
+=====================================+=====================+=====================+
|RAX-AUTH:domains                     |Object *(Required)*  |The collection of    |
|                                     |                     |``domains`` that the |
|                                     |                     |authenticated user   |
|                                     |                     |has permission to    |
|                                     |                     |view.                |
+-------------------------------------+---------------------+---------------------+
|RAX-AUTH:domain                      |Object *(Required)*  |An object that       |
|                                     |                     |contains the domain  |
|                                     |                     |configuration        |
|                                     |                     |attribute settings.  |
+-------------------------------------+---------------------+---------------------+
|RAX-AUTH:domain.\ **id**             |String *(Required)*  |The unique id for    |
|                                     |                     |the domain.          |
+-------------------------------------+---------------------+---------------------+
|RAX-AUTH:domain.\ **enabled**        |Boolean *(Optional)* |Indicates whether    |
|                                     |                     |the domain is        |
|                                     |                     |enabled.             |
+-------------------------------------+---------------------+---------------------+
|RAX-AUTH:domain.\                    |String *(Optional)*  |The domain           |
|**rax-auth:description**             |                     |description.         |
+-------------------------------------+---------------------+---------------------+
|RAX-AUTH:domain.\                    |String *(Optional)*  |The domain name.     |
|**name**                             |                     |                     |
+-------------------------------------+---------------------+---------------------+
|RAX-AUTH:domain.\                    |String *(Optional)*  |The Rackspace        |
|**rackspaceCustomerNumber**          |                     |customer number.     |
+-------------------------------------+---------------------+---------------------+
|RAX-AUTH:domain.\                    |String *(Optional)*  |If present, this     |
|**domainMultiFactorEnforcementLevel**|                     |extended attribute   |
|                                     |                     |specifies the multi- |
|                                     |                     |factor               |
|                                     |                     |authentication       |
|                                     |                     |enforcement policy   |
|                                     |                     |that applies to      |
|                                     |                     |accounts within the  |
|                                     |                     |specified domain. *  |
|                                     |                     |``REQUIRED`` Users   |
|                                     |                     |within the domain    |
|                                     |                     |must use multi-      |
|                                     |                     |factor               |
|                                     |                     |authentication to    |
|                                     |                     |access their         |
|                                     |                     |account. *           |
|                                     |                     |``OPTIONAL`` Users   |
|                                     |                     |have the option to   |
|                                     |                     |authenticate using   |
|                                     |                     |multi-factor         |
|                                     |                     |authentication.      |
+-------------------------------------+---------------------+---------------------+


**Example: List domains HTTP and XML response**

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/xml

.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <rax-auth:domains
        xmlns:atom="http://www.w3.org/2005/Atom"
        xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
        xmlns="http://docs.openstack.org/identity/api/v2.0"
        xmlns:ns4="http://docs.rackspace.com/identity/api/ext/RAX-KSGRP/v1.0"
        xmlns:rax-ksqa="http://docs.rackspace.com/identity/api/ext/RAX-KSQA/v1.0"
        xmlns:os-ksadm="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
        xmlns:rax-kskey="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"
        xmlns:os-ksec2="http://docs.openstack.org/identity/api/ext/OS-KSEC2/v1.0">
        <rax-auth:domain enabled="true" id="9883948" name="GCorp" rackspaceCustomerNumber="RCN-123-123-123">
            <rax-auth:description>A very good customer</rax-auth:description>
        </rax-auth:domain>
        <rax-auth:domain enabled="true" id="111" name="Azuri">
            <rax-auth:description>High profile</rax-auth:description>
        </rax-auth:domain>
        <rax-auth:domain enabled="true" id="222" name="GCorp"/>
   </rax-auth:domain>


**Example: List domains HTTP and JSON response**

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json

.. code::

   {
       "RAX-AUTH:domains": {
           "rax-auth:domain": [
               {
                   "id": "9883948",
                   "enabled": true,
                   "description": "A very good customer",
                   "name": "GCorp",
                   "rackspaceCustomerNumber": "RCN-123-123-123",
                   "domainMultiFactorEnforcementLevel": "OPTIONAL"
               },
               {
                   "id": "111",
                   "enabled": true,
                   "description": "High profile",
                   "name": "Azuri"
               },
               {
                   "id": "222",
                   "enabled": true,
                   "name": "GCorp"
               }
           ]
       }
   }
