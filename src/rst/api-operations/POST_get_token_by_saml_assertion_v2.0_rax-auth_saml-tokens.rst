=============================================================================
Get Token By Saml Assertion -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Get Token By Saml Assertion
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <POST_get_token_by_saml_assertion_v2.0_rax-auth_saml-tokens.rst#request>`__
`Response <POST_get_token_by_saml_assertion_v2.0_rax-auth_saml-tokens.rst#response>`__

.. code-block:: javascript

    POST /v2.0/RAX-AUTH/saml-tokens

Get a token by SAML assertion.

Cloud Identity supports identity federation through the implementation of the SAML 2 protocol. Using this protocol, you can provide an XML assertion indicating that the identity is already authenticated via a trusted identity provider. Cloud Identity will return a token in response.



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









**Example Token SAML request: XML**


.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <saml2p:Response xmlns:saml2p="urn:oasis:names:tc:SAML:2.0:protocol"
         ID="cedee8c1-22b7-45dc-8dbf-eeb107175eaa" IssueInstant="2013-11-15T16:19:06.313Z"
         Version="2.0" xmlns:xs="http://www.w3.org/2001/XMLSchema">
         <saml2:Issuer xmlns:saml2="urn:oasis:names:tc:SAML:2.0:assertion">https://idp.rackspace.com
         </saml2:Issuer>
         <ds:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">
              <ds:SignedInfo>
                   <ds:CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#" />
                   <ds:SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#rsa-sha1" />
                   <ds:Reference URI="#cedee8c1-22b7-45dc-8dbf-eeb107175eaa">
                        <ds:Transforms>
                             <ds:Transform
                                  Algorithm="http://www.w3.org/2000/09/xmldsig#enveloped-signature" />
                             <ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#">
                                  <ec:InclusiveNamespaces xmlns:ec="http://www.w3.org/2001/10/xml-exc-c14n#"
                                       PrefixList="xs" />
                             </ds:Transform>
                        </ds:Transforms>
                        <ds:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
                        <ds:DigestValue>LtawRPe105g7JDDfbwGrrKQ6/Lk=</ds:DigestValue>
                   </ds:Reference>
              </ds:SignedInfo>
              <ds:SignatureValue>lm+bWLfJO15VEPcGHnJkgLSPXPe+ckPWCDfnvd9UteeL7A8xvSJBb4YGYUIwPqgM9PZU6RTRVmfsM85/Jo4/xA==
              </ds:SignatureValue>
         </ds:Signature>
         <saml2p:Status>
              <saml2p:StatusCode Value="urn:oasis:names:tc:SAML:2.0:status:Success" />
         </saml2p:Status>
         <saml2:Assertion xmlns:saml2="urn:oasis:names:tc:SAML:2.0:assertion"
              ID="406fb7fe-a519-4919-a42c-f67794a670a5" IssueInstant="2013-11-15T16:19:06.310Z"
              Version="2.0">
              <saml2:Issuer>http://my.rackspace.com</saml2:Issuer>
              <saml2:Subject>
                   <saml2:NameID Format="urn:oasis:names:tc:SAML:1.1:nameid-format:unspecified">john.doe</saml2:NameID>
                   <saml2:SubjectConfirmation Method="urn:oasis:names:tc:SAML:2.0:cm:bearer">
                        <saml2:SubjectConfirmationData
                             NotOnOrAfter="2013-11-17T16:19:06.298Z" />
                   </saml2:SubjectConfirmation>
              </saml2:Subject>
              <saml2:AuthnStatement AuthnInstant="2013-11-15T16:19:04.055Z">
                   <saml2:AuthnContext>
                        <saml2:AuthnContextClassRef>urn:oasis:names:tc:SAML:2.0:ac:classes:PasswordProtectedTransport
                        </saml2:AuthnContextClassRef>
                   </saml2:AuthnContext>
              </saml2:AuthnStatement>
              <saml2:AttributeStatement>
                   <saml2:Attribute Name="roles">
                        <saml2:AttributeValue xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                             xsi:type="xs:string">nova:admin</saml2:AttributeValue>
                   </saml2:Attribute>
                   <saml2:Attribute Name="domain">
                        <saml2:AttributeValue xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                             xsi:type="xs:string">323676</saml2:AttributeValue>
                   </saml2:Attribute>
                   <saml2:Attribute Name="email">
                        <saml2:AttributeValue xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                             xsi:type="xs:string">no-reply@rackspace.com</saml2:AttributeValue>
                   </saml2:Attribute>
              </saml2:AttributeStatement>
         </saml2:Assertion>
    </saml2p:Response>
    


Response
^^^^^^^^^^^^^^^^^^





**Example Token SAML response: XML**


.. code::

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <access
         xmlns:os-ksadm="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
         xmlns="http://docs.openstack.org/identity/api/v2.0"
         xmlns:rax-kskey="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"
         xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
         xmlns:rax-ksqa="http://docs.rackspace.com/identity/api/ext/RAX-KSQA/v1.0"
         xmlns:common="http://docs.openstack.org/common/api/v1.0"
         xmlns:ksgrp="http://docs.rackspace.com/identity/api/ext/RAX-KSGRP/v1.0"
         xmlns:rax-kscatalog="http://docs.openstack.org/identity/api/ext/OS-KSCATALOG/v1.0"
         xmlns:atom="http://www.w3.org/2005/Atom">
         <token
              id="aaaaa-bbbbb-ccccc-dddd"
              expires="2012-04-13T13:15:00.000-05:00">
              <tenant id="12345" name="12345"/>
              <rax-auth:authenticatedBy>
                   <rax-auth:credential>FEDERATED</rax-auth:credential>
              </rax-auth:authenticatedBy>
         </token>
         <user
              xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
              id="161418" name="john.doe" rax-auth:defaultRegion="DFW" rax-auth:federatedIdp="https://idp.rackspace.com">
              <roles>
                   <role id="3" name="identity:default"
                        description="Default Role."/>
                   <role id="208" name="nova:admin"
                        description="Nova Admin."/>
              </roles>
         </user>
         <serviceCatalog>
              <service type="rax:database" name="cloudDatabases">
                   <endpoint region="DFW" tenantId="12345"
                        publicURL="https://dfw.databases.api.rackspacecloud.com/v1.0/12345"/>
              </service>
              <service type="rax:object-cdn" name="cloudFilesCDN">
                   <endpoint region="DFW" tenantId="MossoCloudFS_aaaa-bbbbbb-ccccc-ddddd"
                        publicURL="https://cdn1.clouddrive.com/v1/MossoCloudFS_aaaa-bbbbbb-ccccc-ddddd"/>
              </service>
              <service type="rax:monitor" name="cloudMonitoring">
                   <endpoint tenantId="12345"
                        publicURL="https://monitoring.api.rackspacecloud.com/v1.0/12345"/>
              </service>
              <service type="object-store" name="cloudFiles">
                   <endpoint region="DFW" tenantId="MossoCloudFS_aaaa-bbbbbb-ccccc-ddddd"
                        publicURL="https://storage101.dfw1.clouddrive.com/v1/MossoCloudFS_aaaa-bbbbbb-ccccc-ddddd"
                        internalURL="https://snet-storage101.dfw1.clouddrive.com/v1/MossoCloudFS_aaaa-bbbbbb-ccccc-ddddd"/>
              </service>
              <service type="compute" name="cloudServers">
                   <endpoint tenantId="12345"
                        publicURL="https://servers.api.rackspacecloud.com/v1.0/12345">
                        <version id="1.0" info="https://servers.api.rackspacecloud.com/v1.0"
                             list="https://servers.api.rackspacecloud.com/"/>
                   </endpoint>
              </service>
              <service type="compute" name="cloudServersOpenStack">
                   <endpoint region="DFW" tenantId="12345"
                        publicURL="https://dfw.servers.api.rackspacecloud.com/v2/12345">
                        <version id="2" info="https://dfw.servers.api.rackspacecloud.com/v2"
                             list="https://dfw.servers.api.rackspacecloud.com/"/>
                   </endpoint>
              </service>
              <service type="rax:dns" name="cloudDNS">
                   <endpoint tenantId="12345"
                        publicURL="https://dns.api.rackspacecloud.com/v1.0/12345"/>
              </service>
         </serviceCatalog>
    </access>


**Example Token SAML response: JSON**


.. code::

    {
        "access": {
            "serviceCatalog": [
                {
                    "endpoints": [
                        {
                            "publicURL": "https://dfw.servers.api.rackspacecloud.com/v2/12345",
                            "region": "DFW",
                            "tenantId": "12345",
                            "versionId": "2",
                            "versionInfo": "https://dfw.servers.api.rackspacecloud.com/v2",
                            "versionList": "https://dfw.servers.api.rackspacecloud.com/"
                        }
                    ],
                    "name": "cloudServersOpenStack",
                    "type": "compute"
                },
                {
                    "endpoints": [
                        {
                            "publicURL": "https://dfw.databases.api.rackspacecloud.com/v1.0/12345",
                            "region": "DFW",
                            "tenantId": "12345"
                        }
                    ],
                    "name": "cloudDatabases",
                    "type": "rax:database"
                },
                {
                    "endpoints": [
                        {
                            "publicURL": "https://dfw.loadbalancers.api.rackspacecloud.com/v1.0/12345",
                            "region": "DFW",
                            "tenantId": "12345"
                        }
                    ],
                    "name": "cloudLoadBalancers",
                    "type": "rax:load-balancer"
                },
                {
                    "endpoints": [
                        {
                            "publicURL": "https://cdn1.clouddrive.com/v1/MossoCloudFS_aaaa-bbbb-cccc ",
                            "region": "DFW",
                            "tenantId": "MossoCloudFS_aaaa-bbbb-cccc "
                        },
                    ],
                    "name": "cloudFilesCDN",
                    "type": "rax:object-cdn"
                },
                {
                    "endpoints": [
                        {
                            "publicURL": "https://dns.api.rackspacecloud.com/v1.0/12345",
                            "tenantId": "12345"
                        }
                    ],
                    "name": "cloudDNS",
                    "type": "rax:dns"
                },
                {
                    "endpoints": [
                        {
                            "publicURL": "https://servers.api.rackspacecloud.com/v1.0/12345",
                            "tenantId": "12345",
                            "versionId": "1.0",
                            "versionInfo": "https://servers.api.rackspacecloud.com/v1.0",
                            "versionList": "https://servers.api.rackspacecloud.com/"
                        }
                    ],
                    "name": "cloudServers",
                    "type": "compute"
                },
                {
                    "endpoints": [
                        {
                            "publicURL": "https://monitoring.api.rackspacecloud.com/v1.0/12345",
                            "tenantId": "12345"
                        }
                    ],
                    "name": "cloudMonitoring",
                    "type": "rax:monitor"
                },
                {
                    "endpoints": [
                        {
                            "internalURL": "https://snet-storage101.dfw1.clouddrive.com/v1/MossoCloudFS_aaaa-bbbb-cccc ",
                            "publicURL": "https://storage101.dfw1.clouddrive.com/v1/MossoCloudFS_aaaa-bbbb-cccc ",
                            "region": "DFW",
                            "tenantId": "MossoCloudFS_aaaa-bbbb-cccc"
                        }
                    ],
                    "name": "cloudFiles",
                    "type": "object-store"
                }
            ],
            "token": {
                "RAX-AUTH:authenticatedBy": [
                    "FEDERATED"
                ],
                "expires": "2012-04-13T13:15:00.000-05:00",
                "id": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
                "tenant": {
                    "id": "12345",
                    "name": "12345"
                }
            },
            "user": {
                "RAX-AUTH:defaultRegion": "DFW",
                "id": "161418",
                "name": "john.doe",
                "RAX-AUTH:federatedIdp": "https://idp.rackspace.com",
                "roles": [
                    {
                        "description": "Default Role.",
                        "id": "3",
                        "name": "identity:default"
                    },
                    {
                        "description": "Nova Admin",
                        "id": "208",
                        "name": "nova:admin"
                    }
                ]
            }
        }
    }

