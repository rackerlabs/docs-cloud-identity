.. _annotated-auth-req-resp:

=============================================
Annotated authentication request and response
=============================================

This section provides sample authentication request and response examples
with detailed information about the values returned in the authentication
response body.

.. contents::
   :local:
   :depth: 2


..  note::

    To learn more about authentication, see the following information:

    -  :ref:`Getting Started <getting-started-guide>` provides instructions for
       submitting an authentication request.

    - :ref:`Token operations <token-operations>` API reference pages provide
      information about other authentication methods and more examples.


.. _sample-auth-req:

Sample request
~~~~~~~~~~~~~~~

The following authentication :ref:`JSON <example-auth-req-json>` and
:ref:`XML <example-auth-req-xml>` examples show the authentication header
and request body for the POST tokens API operation. When you authenticate,
use your own credentials for user name and API key rather than the sample
values shown in the examples.  For attribute descriptions, see the
authentication request attribute descriptions in the  table following
the examples.


.. _example-auth-req-json:

**Example: Authentication request with headers: JSON**

.. code::

   POST /v2.0/tokens HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Content-Type: application/json
   Accept: application/json

   {"auth":
     {"RAX-KSKEY:apiKeyCredentials":
        {"username":"yourUserName",
          "apiKey":"a4bbc55a951242c48b03e88e32123456"}
     }
   }


.. _example-auth-req-xml:

**Example: Authentication request with headers: XML**

.. code::

   POST /v2.0/tokens HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Content-Type: application/xml
   Accept: application/xml

   <auth>
     <apiKeyCredentials
          xmlns="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"
          username="yourUserName"
          apiKey="a4bbc55a951242c48b03e88e32123456"/>
     </auth>


.. _auth-req-obj-attribs:

**Table: Authentication request attribute descriptions**

+-----------------------------+------------+-------------------------------------------------------------------------------------+
| Attribute                   | Type       | Description                                                                         |
+-----------------------------+------------+-------------------------------------------------------------------------------------+
| auth                        | Object     | The auth object provides the credentials for the authentication request.            |
+-----------------------------+------------+-------------------------------------------------------------------------------------+
| RAX-KSKEY:apiKeyCredentials | String     | The API key associated with the Rackspace Cloud account. You                        |
|                             |            | can find your API key on the Account Settings page in the                           |
|                             |            | Cloud Control panel.                                                                |
|                             |            |                                                                                     |
|                             |            | After logging in, click your user ID. Then, select                                  |
|                             |            | **Account Settings** from the                                                       |
|                             |            | menu. You can authenticate using other credentials like                             |
|                             |            | password or multi-factor authentication passcode. For details,                      |
|                             |            | see the Tokens API operation reference.                                             |
+-----------------------------+------------+-------------------------------------------------------------------------------------+
| username                    | String     | This value is the user name that you use to log in to the Rackspace                 |
|                             |            | Cloud Control Panel at https://mycloud.rackspace.com.                               |
+-----------------------------+------------+-------------------------------------------------------------------------------------+
| tenantId                    | String     | Some services have multiple layers of authentication, with service-specific         |
|                             | (Optional) | credentials in addition to vendor-specific credentials. In such cases, associating  |
|                             |            | a user with a tenant can be a method of passing that additional level of            |
|                             |            | identifying information to the service.                                             |
+-----------------------------+------------+-------------------------------------------------------------------------------------+


.. _samp-auth-resp:

Sample response
~~~~~~~~~~~~~~~

When you submit a **POST tokens** authentication request with valid
credentials, the Identity service returns a response. The following
authentication :ref:`JSON <example-auth-resp-json>` and
:ref:`XML <example-auth-resp-xml>` examples show the
entire authentication response header and body content.

The sections that follow these examples provide detailed information
about the following parts of the response:

-  **Token resource.**
   The :ref:`token object <auth-resp-token-resource>` returns
   a scoped authentication token that can be used to access Rackspace
   Cloud services for the specified tenant. Token scope is determined by
   tenant and user role assignments for the authenticated user.

-  **Service catalog resource**
   The
   :ref:`service catalog object <svccat-resource>` returns a
   list of service objects that provide the endpoint and description for
   each service that can be accessed using the authentication token.

   If you have questions or issues with the services and endpoints included in the
   catalog, contact Rackspace support.

-  **User resource**
   The :ref:`user object <auth-resp-user-resource>` returns the
   user name, ID, default Cloud service region, and information about
   the roles assigned to the user. User role assignments determine the
   API operations available to a user after authenticating to a
   Rackspace Cloud service.


.. _example-auth-resp-json:

**Example: Authentication response: JSON**

.. code::

    {
        "access": {
            "token": {
                "id": "d74f592f986e4d6e995853ccf0123456",
                "expires": "2015-06-05T16:24:57.637Z",
                "tenant": {
                    "id": "123456",
                    "name": "123456"
                },
                "RAX-AUTH:authenticatedBy": [
                    "APIKEY"
                ]
            },
            "serviceCatalog": [
                {
                    "name": "cloudBlockStorage",
                    "endpoints": [
                        {
                            "region": "SYD",
                            "tenantId": "123456",
                            "publicURL": "https://syd.blockstorage.api.rackspacecloud.com/v1/123456"
                        },
                        {
                            "region": "DFW",
                            "tenantId": "123456",
                            "publicURL": "https://dfw.blockstorage.api.rackspacecloud.com/v1/123456"
                        },
                        {
                            "region": "IAD",
                            "tenantId": "123456",
                            "publicURL": "https://iad.blockstorage.api.rackspacecloud.com/v1/123456"
                        },
                        {
                            "region": "HKG",
                            "tenantId": "123456",
                            "publicURL": "https://hkg.blockstorage.api.rackspacecloud.com/v1/123456"
                        }
                    ],
                    "type": "volume"
                },
                {
                    "name": "cloudImages",
                    "endpoints": [
                        {
                            "region": "IAD",
                            "tenantId": "123456",
                            "publicURL": "https://iad.images.api.rackspacecloud.com/v2"
                        },
                        {
                            "region": "HKG",
                            "tenantId": "123456",
                            "publicURL": "https://hkg.images.api.rackspacecloud.com/v2"
                        },
                        {
                            "region": "DFW",
                            "tenantId": "123456",
                            "publicURL": "https://dfw.images.api.rackspacecloud.com/v2"
                        },
                        {
                            "region": "SYD",
                            "tenantId": "123456",
                            "publicURL": "https://syd.images.api.rackspacecloud.com/v2"
                        }
                    ],
                    "type": "image"
                },
                {
                    "name": "cloudQueues",
                    "endpoints": [
                        {
                            "region": "HKG",
                            "tenantId": "123456",
                            "publicURL": "https://hkg.queues.api.rackspacecloud.com/v1/123456",
                            "internalURL": "https://snet-hkg.queues.api.rackspacecloud.com/v1/123456"
                        },
                        {
                            "region": "SYD",
                            "tenantId": "123456",
                            "publicURL": "https://syd.queues.api.rackspacecloud.com/v1/123456",
                            "internalURL": "https://snet-syd.queues.api.rackspacecloud.com/v1/123456"
                        },
                        {
                            "region": "DFW",
                            "tenantId": "123456",
                            "publicURL": "https://dfw.queues.api.rackspacecloud.com/v1/123456",
                            "internalURL": "https://snet-dfw.queues.api.rackspacecloud.com/v1/123456"
                        },
                        {
                            "region": "IAD",
                            "tenantId": "123456",
                            "publicURL": "https://iad.queues.api.rackspacecloud.com/v1/123456",
                            "internalURL": "https://snet-iad.queues.api.rackspacecloud.com/v1/123456"
                        }
                    ],
                    "type": "rax:queues"
                },
                {
                    "name": "cloudBigData",
                    "endpoints": [
                        {
                            "region": "IAD",
                            "tenantId": "123456",
                            "publicURL": "https://iad.bigdata.api.rackspacecloud.com/v1.0/123456"
                        },
                        {
                            "region": "DFW",
                            "tenantId": "123456",
                            "publicURL": "https://dfw.bigdata.api.rackspacecloud.com/v1.0/123456"
                        }
                    ],
                    "type": "rax:bigdata"
                },
                {
                    "name": "cloudOrchestration",
                    "endpoints": [
                        {
                            "region": "HKG",
                            "tenantId": "123456",
                            "publicURL": "https://hkg.orchestration.api.rackspacecloud.com/v1/123456"
                        },
                        {
                            "region": "DFW",
                            "tenantId": "123456",
                            "publicURL": "https://dfw.orchestration.api.rackspacecloud.com/v1/123456"
                        },
                        {
                            "region": "IAD",
                            "tenantId": "123456",
                            "publicURL": "https://iad.orchestration.api.rackspacecloud.com/v1/123456"
                        },
                        {
                            "region": "SYD",
                            "tenantId": "123456",
                            "publicURL": "https://syd.orchestration.api.rackspacecloud.com/v1/123456"
                        }
                    ],
                    "type": "orchestration"
                },
                {
                    "name": "cloudServersOpenStack",
                    "endpoints": [
                        {
                            "region": "SYD",
                            "tenantId": "123456",
                            "publicURL": "https://syd.servers.api.rackspacecloud.com/v2/123456",
                            "versionInfo": "https://syd.servers.api.rackspacecloud.com/v2",
                            "versionList": "https://syd.servers.api.rackspacecloud.com/",
                            "versionId": "2"
                        },
                        {
                            "region": "DFW",
                            "tenantId": "123456",
                            "publicURL": "https://dfw.servers.api.rackspacecloud.com/v2/123456",
                            "versionInfo": "https://dfw.servers.api.rackspacecloud.com/v2",
                            "versionList": "https://dfw.servers.api.rackspacecloud.com/",
                            "versionId": "2"
                        },
                        {
                            "region": "IAD",
                            "tenantId": "123456",
                            "publicURL": "https://iad.servers.api.rackspacecloud.com/v2/123456",
                            "versionInfo": "https://iad.servers.api.rackspacecloud.com/v2",
                            "versionList": "https://iad.servers.api.rackspacecloud.com/",
                            "versionId": "2"
                        },
                        {
                            "region": "HKG",
                            "tenantId": "123456",
                            "publicURL": "https://hkg.servers.api.rackspacecloud.com/v2/123456",
                            "versionInfo": "https://hkg.servers.api.rackspacecloud.com/v2",
                            "versionList": "https://hkg.servers.api.rackspacecloud.com/",
                            "versionId": "2"
                        }
                    ],
                    "type": "compute"
                },
                {
                    "name": "autoscale",
                    "endpoints": [
                        {
                            "region": "DFW",
                            "tenantId": "123456",
                            "publicURL": "https://dfw.autoscale.api.rackspacecloud.com/v1.0/123456"
                        },
                        {
                            "region": "HKG",
                            "tenantId": "123456",
                            "publicURL": "https://hkg.autoscale.api.rackspacecloud.com/v1.0/123456"
                        },
                        {
                            "region": "IAD",
                            "tenantId": "123456",
                            "publicURL": "https://iad.autoscale.api.rackspacecloud.com/v1.0/123456"
                        },
                        {
                            "region": "SYD",
                            "tenantId": "123456",
                            "publicURL": "https://syd.autoscale.api.rackspacecloud.com/v1.0/123456"
                        }
                    ],
                    "type": "rax:autoscale"
                },
                {
                    "name": "cloudDatabases",
                    "endpoints": [
                        {
                            "region": "SYD",
                            "tenantId": "123456",
                            "publicURL": "https://syd.databases.api.rackspacecloud.com/v1.0/123456"
                        },
                        {
                            "region": "DFW",
                            "tenantId": "123456",
                            "publicURL": "https://dfw.databases.api.rackspacecloud.com/v1.0/123456"
                        },
                        {
                            "region": "HKG",
                            "tenantId": "123456",
                            "publicURL": "https://hkg.databases.api.rackspacecloud.com/v1.0/123456"
                        }
                    ],
                    "type": "rax:database"
                },
                {
                    "name": "cloudBackup",
                    "endpoints": [
                        {
                            "region": "IAD",
                            "tenantId": "123456",
                            "publicURL": "https://iad.backup.api.rackspacecloud.com/v1.0/123456"
                        },
                        {
                            "region": "HKG",
                            "tenantId": "123456",
                            "publicURL": "https://hkg.backup.api.rackspacecloud.com/v1.0/123456"
                        },
                        {
                            "region": "SYD",
                            "tenantId": "123456",
                            "publicURL": "https://syd.backup.api.rackspacecloud.com/v1.0/123456"
                        },
                        {
                            "region": "DFW",
                            "tenantId": "123456",
                            "publicURL": "https://dfw.backup.api.rackspacecloud.com/v1.0/123456"
                        }
                    ],
                    "type": "rax:backup"
                },
                {
                    "name": "cloudNetworks",
                    "endpoints": [
                        {
                            "region": "IAD",
                            "tenantId": "123456",
                            "publicURL": "https://iad.networks.api.rackspacecloud.com/v2.0"
                        },
                        {
                            "region": "LON",
                            "tenantId": "123456",
                            "publicURL": "https://lon.networks.api.rackspacecloud.com/v2.0"
                        },
                        {
                            "region": "SYD",
                            "tenantId": "123456",
                            "publicURL": "https://syd.networks.api.rackspacecloud.com/v2.0"
                        },
                        {
                            "region": "DFW",
                            "tenantId": "123456",
                            "publicURL": "https://dfw.networks.api.rackspacecloud.com/v2.0"
                        },
                        {
                            "region": "HKG",
                            "tenantId": "123456",
                            "publicURL": "https://hkg.networks.api.rackspacecloud.com/v2.0"
                        }
                    ],
                    "type": "network"
                },
                {
                    "name": "cloudMetrics",
                    "endpoints": [
                        {
                            "region": "IAD",
                            "tenantId": "123456",
                            "publicURL": "https://global.metrics.api.rackspacecloud.com/v2.0/123456"
                        }
                    ],
                    "type": "rax:cloudmetrics"
                },
                {
                    "name": "cloudLoadBalancers",
                    "endpoints": [
                        {
                            "region": "SYD",
                            "tenantId": "123456",
                            "publicURL": "https://syd.loadbalancers.api.rackspacecloud.com/v1.0/123456"
                        },
                        {
                            "region": "IAD",
                            "tenantId": "123456",
                            "publicURL": "https://iad.loadbalancers.api.rackspacecloud.com/v1.0/123456"
                        },
                        {
                            "region": "HKG",
                            "tenantId": "123456",
                            "publicURL": "https://hkg.loadbalancers.api.rackspacecloud.com/v1.0/123456"
                        },
                        {
                            "region": "DFW",
                            "tenantId": "123456",
                            "publicURL": "https://dfw.loadbalancers.api.rackspacecloud.com/v1.0/123456"
                        }
                    ],
                    "type": "rax:load-balancer"
                },
                {
                    "name": "cloudFeeds",
                    "endpoints": [
                        {
                            "region": "HKG",
                            "tenantId": "123456",
                            "publicURL": "https://hkg.feeds.api.rackspacecloud.com/123456",
                            "internalURL": "https://atom.prod.hkg1.us.ci.rackspace.net/123456"
                        },
                        {
                            "region": "SYD",
                            "tenantId": "123456",
                            "publicURL": "https://syd.feeds.api.rackspacecloud.com/123456",
                            "internalURL": "https://atom.prod.syd2.us.ci.rackspace.net/123456"
                        },
                        {
                            "region": "IAD",
                            "tenantId": "123456",
                            "publicURL": "https://iad.feeds.api.rackspacecloud.com/123456",
                            "internalURL": "https://atom.prod.iad3.us.ci.rackspace.net/123456"
                        },
                        {
                            "region": "DFW",
                            "tenantId": "123456",
                            "publicURL": "https://dfw.feeds.api.rackspacecloud.com/123456",
                            "internalURL": "https://atom.prod.dfw1.us.ci.rackspace.net/123456"
                        }
                    ],
                    "type": "rax:feeds"
                },
                {
                    "name": "cloudMonitoring",
                    "endpoints": [
                        {
                            "tenantId": "123456",
                            "publicURL": "https://monitoring.api.rackspacecloud.com/v1.0/123456"
                        }
                    ],
                    "type": "rax:monitor"
                },
                {
                    "name": "cloudDNS",
                    "endpoints": [
                        {
                            "tenantId": "123456",
                            "publicURL": "https://dns.api.rackspacecloud.com/v1.0/123456"
                        }
                    ],
                    "type": "rax:dns"
                },
                {
                    "name": "cloudServers",
                    "endpoints": [
                        {
                            "tenantId": "123456",
                            "publicURL": "https://servers.api.rackspacecloud.com/v1.0/123456",
                            "versionInfo": "https://servers.api.rackspacecloud.com/v1.0",
                            "versionList": "https://servers.api.rackspacecloud.com/",
                            "versionId": "1.0"
                        }
                    ],
                    "type": "compute"
                },
                {
                    "name": "rackCDN",
                    "endpoints": [
                        {
                            "region": "DFW",
                            "tenantId": "123456",
                            "publicURL": "https://global.cdn.api.rackspacecloud.com/v1.0/123456",
                            "internalURL": "https://global.cdn.api.rackspacecloud.com/v1.0/123456"
                        }
                    ],
                    "type": "rax:cdn"
                },
                {
                    "name": "cloudFilesCDN",
                    "endpoints": [
                        {
                            "region": "DFW",
                            "tenantId": "MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f",
                            "publicURL": "https://cdn1.clouddrive.com/v1/MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f"
                        },
                        {
                            "region": "SYD",
                            "tenantId": "MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f",
                            "publicURL": "https://cdn4.clouddrive.com/v1/MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f"
                        },
                        {
                            "region": "HKG",
                            "tenantId": "MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f",
                            "publicURL": "https://cdn6.clouddrive.com/v1/MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f"
                        },
                        {
                            "region": "IAD",
                            "tenantId": "MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f",
                            "publicURL": "https://cdn5.clouddrive.com/v1/MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f"
                        }
                    ],
                    "type": "rax:object-cdn"
                },
                {
                    "name": "cloudFiles",
                    "endpoints": [
                        {
                            "region": "DFW",
                            "tenantId": "MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f",
                            "publicURL": "https://storage101.dfw1.clouddrive.com/v1/MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f",
                            "internalURL": "https://snet-storage101.dfw1.clouddrive.com/v1/MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f"
                        },
                        {
                            "region": "SYD",
                            "tenantId": "MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f",
                            "publicURL": "https://storage101.syd2.clouddrive.com/v1/MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f",
                            "internalURL": "https://snet-storage101.syd2.clouddrive.com/v1/MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f"
                        },
                        {
                            "region": "IAD",
                            "tenantId": "MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f",
                            "publicURL": "https://storage101.iad3.clouddrive.com/v1/MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f",
                            "internalURL": "https://snet-storage101.iad3.clouddrive.com/v1/MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f"
                        },
                        {
                            "region": "HKG",
                            "tenantId": "MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f",
                            "publicURL": "https://storage101.hkg1.clouddrive.com/v1/MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f",
                            "internalURL": "https://snet-storage101.hkg1.clouddrive.com/v1/MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f"
                        }
                    ],
                    "type": "object-store"
                }
            ],
            "user": {
                "id": "172157",
                "roles": [
                    {
                        "id": "10000150",
                        "description": "Checkmate Access role",
                        "name": "checkmate"
                    },
                    {
                        "tenantId": "MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f",
                        "id": "5",
                        "description": "A Role that allows a user access to keystone Service methods",
                        "name": "object-store:default"
                    },
                    {
                        "tenantId": "123456",
                        "id": "6",
                        "description": "A Role that allows a user access to keystone Service methods",
                        "name": "compute:default"
                    },
                    {
                        "id": "3",
                        "description": "User Admin Role.",
                        "name": "identity:user-admin"
                    }
                ],
                "name": "yourUserName",
                "RAX-AUTH:defaultRegion": "DFW",
                "RAX-AUTH:sessionInactivityTimeout": "PT15M"
            }
        }
    }


.. _example-auth-resp-xml:

**Example: Authentication response: XML**

.. code::

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <access
        xmlns:atom="http://www.w3.org/2005/Atom"
        xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
        xmlns="http://docs.openstack.org/identity/api/v2.0"
        xmlns:ns4="http://docs.rackspace.com/identity/api/ext/RAX-KSGRP/v1.0"
        xmlns:rax-ksqa="http://docs.rackspace.com/identity/api/ext/RAX-KSQA/v1.0"
        xmlns:os-ksadm="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
        xmlns:rax-kskey="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"
        xmlns:os-ksec2="http://docs.openstack.org/identity/api/ext/OS-KSEC2/v1.0">
        <token id="d74f592f986e4d6e995853ccf01d25fe" expires="2015-06-05T16:24:57.637Z">
            <tenant id="123456" name="123456"/>
            <rax-auth:authenticatedBy>
                <rax-auth:credential>APIKEY</rax-auth:credential>
            </rax-auth:authenticatedBy>
        </token>
        <user id="172157" name="yourUserName" rax-auth:defaultRegion="DFW" rax-auth:sessionInactivityTimeout="PT15M">
            <roles>
                <role id="10000150" name="checkmate" description="Checkmate Access role" rax-auth:propagate="false"/>
                <role id="5" name="object-store:default" description="A Role that allows a user access to keystone Service methods"
                    tenantId="MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f" rax-auth:propagate="true"/>
                <role id="6" name="compute:default" description="A Role that allows a user access to keystone Service methods"
                    tenantId="123456" rax-auth:propagate="true"/>
                <role id="3" name="identity:user-admin" description="User Admin Role." rax-auth:propagate="false"/>
            </roles>
        </user>
        <serviceCatalog>
            <service type="volume" name="cloudBlockStorage">
                <endpoint region="SYD" tenantId="123456" publicURL="https://syd.blockstorage.api.rackspacecloud.com/v1/123456"/>
                <endpoint region="DFW" tenantId="123456" publicURL="https://dfw.blockstorage.api.rackspacecloud.com/v1/123456"/>
                <endpoint region="IAD" tenantId="123456" publicURL="https://iad.blockstorage.api.rackspacecloud.com/v1/123456"/>
                <endpoint region="HKG" tenantId="123456" publicURL="https://hkg.blockstorage.api.rackspacecloud.com/v1/123456"/>
            </service>
            <service type="image" name="cloudImages">
                <endpoint region="IAD" tenantId="123456" publicURL="https://iad.images.api.rackspacecloud.com/v2"/>
                <endpoint region="HKG" tenantId="123456" publicURL="https://hkg.images.api.rackspacecloud.com/v2"/>
                <endpoint region="DFW" tenantId="123456" publicURL="https://dfw.images.api.rackspacecloud.com/v2"/>
                <endpoint region="SYD" tenantId="123456" publicURL="https://syd.images.api.rackspacecloud.com/v2"/>
            </service>
            <service type="rax:queues" name="cloudQueues">
                <endpoint region="HKG" tenantId="123456" publicURL="https://hkg.queues.api.rackspacecloud.com/v1/123456"
                    internalURL="https://snet-hkg.queues.api.rackspacecloud.com/v1/123456"/>
                <endpoint region="SYD" tenantId="123456" publicURL="https://syd.queues.api.rackspacecloud.com/v1/123456"
                    internalURL="https://snet-syd.queues.api.rackspacecloud.com/v1/123456"/>
                <endpoint region="DFW" tenantId="123456" publicURL="https://dfw.queues.api.rackspacecloud.com/v1/123456"
                    internalURL="https://snet-dfw.queues.api.rackspacecloud.com/v1/123456"/>
                <endpoint region="IAD" tenantId="123456" publicURL="https://iad.queues.api.rackspacecloud.com/v1/123456"
                    internalURL="https://snet-iad.queues.api.rackspacecloud.com/v1/123456"/>
            </service>
            <service type="rax:bigdata" name="cloudBigData">
                <endpoint region="IAD" tenantId="123456" publicURL="https://iad.bigdata.api.rackspacecloud.com/v1.0/123456"/>
                <endpoint region="DFW" tenantId="123456" publicURL="https://dfw.bigdata.api.rackspacecloud.com/v1.0/123456"/>
            </service>
            <service type="orchestration" name="cloudOrchestration">
                <endpoint region="HKG" tenantId="123456" publicURL="https://hkg.orchestration.api.rackspacecloud.com/v1/123456"/>
                <endpoint region="DFW" tenantId="123456" publicURL="https://dfw.orchestration.api.rackspacecloud.com/v1/123456"/>
                <endpoint region="IAD" tenantId="123456" publicURL="https://iad.orchestration.api.rackspacecloud.com/v1/123456"/>
                <endpoint region="SYD" tenantId="123456" publicURL="https://syd.orchestration.api.rackspacecloud.com/v1/123456"/>
            </service>
            <service type="compute" name="cloudServersOpenStack">
                <endpoint region="SYD" tenantId="123456" publicURL="https://syd.servers.api.rackspacecloud.com/v2/123456">
                    <version id="2" info="https://syd.servers.api.rackspacecloud.com/v2" list="https://syd.servers.api.rackspacecloud.com/"/>
                </endpoint>
                <endpoint region="DFW" tenantId="123456" publicURL="https://dfw.servers.api.rackspacecloud.com/v2/123456">
                    <version id="2" info="https://dfw.servers.api.rackspacecloud.com/v2" list="https://dfw.servers.api.rackspacecloud.com/"/>
                </endpoint>
                <endpoint region="IAD" tenantId="123456" publicURL="https://iad.servers.api.rackspacecloud.com/v2/123456">
                    <version id="2" info="https://iad.servers.api.rackspacecloud.com/v2" list="https://iad.servers.api.rackspacecloud.com/"/>
                </endpoint>
                <endpoint region="HKG" tenantId="123456" publicURL="https://hkg.servers.api.rackspacecloud.com/v2/123456">
                    <version id="2" info="https://hkg.servers.api.rackspacecloud.com/v2" list="https://hkg.servers.api.rackspacecloud.com/"/>
                </endpoint>
            </service>
            <service type="rax:autoscale" name="autoscale">
                <endpoint region="DFW" tenantId="123456" publicURL="https://dfw.autoscale.api.rackspacecloud.com/v1.0/123456"/>
                <endpoint region="HKG" tenantId="123456" publicURL="https://hkg.autoscale.api.rackspacecloud.com/v1.0/123456"/>
                <endpoint region="IAD" tenantId="123456" publicURL="https://iad.autoscale.api.rackspacecloud.com/v1.0/123456"/>
                <endpoint region="SYD" tenantId="123456" publicURL="https://syd.autoscale.api.rackspacecloud.com/v1.0/123456"/>
            </service>
            <service type="rax:database" name="cloudDatabases">
                <endpoint region="SYD" tenantId="123456" publicURL="https://syd.databases.api.rackspacecloud.com/v1.0/123456"/>
                <endpoint region="DFW" tenantId="123456" publicURL="https://dfw.databases.api.rackspacecloud.com/v1.0/123456"/>
                <endpoint region="IAD" tenantId="123456" publicURL="https://iad.databases.api.rackspacecloud.com/v1.0/123456"/>
                <endpoint region="HKG" tenantId="123456" publicURL="https://hkg.databases.api.rackspacecloud.com/v1.0/123456"/>
            </service>
            <service type="rax:backup" name="cloudBackup">
                <endpoint region="IAD" tenantId="123456" publicURL="https://iad.backup.api.rackspacecloud.com/v1.0/123456"/>
                <endpoint region="HKG" tenantId="123456" publicURL="https://hkg.backup.api.rackspacecloud.com/v1.0/123456"/>
                <endpoint region="SYD" tenantId="123456" publicURL="https://syd.backup.api.rackspacecloud.com/v1.0/123456"/>
                <endpoint region="DFW" tenantId="123456" publicURL="https://dfw.backup.api.rackspacecloud.com/v1.0/123456"/>
            </service>
            <service type="network" name="cloudNetworks">
                <endpoint region="IAD" tenantId="123456" publicURL="https://iad.networks.api.rackspacecloud.com/v2.0"/>
                <endpoint region="LON" tenantId="123456" publicURL="https://lon.networks.api.rackspacecloud.com/v2.0"/>
                <endpoint region="SYD" tenantId="123456" publicURL="https://syd.networks.api.rackspacecloud.com/v2.0"/>
                <endpoint region="DFW" tenantId="123456" publicURL="https://dfw.networks.api.rackspacecloud.com/v2.0"/>
                <endpoint region="HKG" tenantId="123456" publicURL="https://hkg.networks.api.rackspacecloud.com/v2.0"/>
            </service>
            <service type="rax:cloudmetrics" name="cloudMetrics">
                <endpoint region="IAD" tenantId="123456" publicURL="https://global.metrics.api.rackspacecloud.com/v2.0/123456"/>
            </service>
            <service type="rax:load-balancer" name="cloudLoadBalancers">
                <endpoint region="SYD" tenantId="123456" publicURL="https://syd.loadbalancers.api.rackspacecloud.com/v1.0/123456"/>
                <endpoint region="IAD" tenantId="123456" publicURL="https://iad.loadbalancers.api.rackspacecloud.com/v1.0/123456"/>
                <endpoint region="HKG" tenantId="123456" publicURL="https://hkg.loadbalancers.api.rackspacecloud.com/v1.0/123456"/>
                <endpoint region="DFW" tenantId="123456" publicURL="https://dfw.loadbalancers.api.rackspacecloud.com/v1.0/123456"/>
            </service>
            <service type="rax:feeds" name="cloudFeeds">
                <endpoint region="HKG" tenantId="123456" publicURL="https://hkg.feeds.api.rackspacecloud.com/123456"
                    internalURL="https://atom.prod.hkg1.us.ci.rackspace.net/123456"/>
                <endpoint region="SYD" tenantId="123456" publicURL="https://syd.feeds.api.rackspacecloud.com/123456"
                    internalURL="https://atom.prod.syd2.us.ci.rackspace.net/123456"/>
                <endpoint region="IAD" tenantId="123456" publicURL="https://iad.feeds.api.rackspacecloud.com/123456"
                    internalURL="https://atom.prod.iad3.us.ci.rackspace.net/123456"/>
                <endpoint region="DFW" tenantId="123456" publicURL="https://dfw.feeds.api.rackspacecloud.com/123456"
                    internalURL="https://atom.prod.dfw1.us.ci.rackspace.net/123456"/>
            </service>
            <service type="rax:monitor" name="cloudMonitoring">
                <endpoint tenantId="123456" publicURL="https://monitoring.api.rackspacecloud.com/v1.0/123456"/>
            </service>
            <service type="rax:dns" name="cloudDNS">
                <endpoint tenantId="123456" publicURL="https://dns.api.rackspacecloud.com/v1.0/123456"/>
            </service>
            <service type="compute" name="cloudServers">
                <endpoint tenantId="123456" publicURL="https://servers.api.rackspacecloud.com/v1.0/123456">
                    <version id="1.0" info="https://servers.api.rackspacecloud.com/v1.0" list="https://servers.api.rackspacecloud.com/"/>
                </endpoint>
            </service>
            <service type="rax:cdn" name="rackCDN">
                <endpoint region="DFW" tenantId="123456" publicURL="https://global.cdn.api.rackspacecloud.com/v1.0/123456"
                    internalURL="https://global.cdn.api.rackspacecloud.com/v1.0/123456"/>
            </service>
            <service type="rax:object-cdn" name="cloudFilesCDN">
                <endpoint region="DFW" tenantId="MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f"
                    publicURL="https://cdn1.clouddrive.com/v1/MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f"/>
                <endpoint region="SYD" tenantId="MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f"
                    publicURL="https://cdn4.clouddrive.com/v1/MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f"/>
                <endpoint region="HKG" tenantId="MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f"
                    publicURL="https://cdn6.clouddrive.com/v1/MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f"/>
                <endpoint region="IAD" tenantId="MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f"
                    publicURL="https://cdn5.clouddrive.com/v1/MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f"/>
            </service>
            <service type="object-store" name="cloudFiles">
                <endpoint region="DFW" tenantId="MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f"
                    publicURL="https://storage101.dfw1.clouddrive.com/v1/MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f"
                    internalURL="https://snet-storage101.dfw1.clouddrive.com/v1/MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f"/>
                <endpoint region="SYD" tenantId="MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f"
                    publicURL="https://storage101.syd2.clouddrive.com/v1/MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f"
                    internalURL="https://snet-storage101.syd2.clouddrive.com/v1/MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f"/>
                <endpoint region="IAD" tenantId="MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f"
                    publicURL="https://storage101.iad3.clouddrive.com/v1/MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f"
                    internalURL="https://snet-storage101.iad3.clouddrive.com/v1/MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f"/>
                <endpoint region="HKG" tenantId="MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f"
                    publicURL="https://storage101.hkg1.clouddrive.com/v1/MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f"
                    internalURL="https://snet-storage101.hkg1.clouddrive.com/v1/MossoCloudFS_9c24e3db-52bf-4f26-8dc1-220871796e9f"/>
            </service>
        </serviceCatalog>
    </access>


.. include:: authentication-ref/token-response-object.rst

.. include:: authentication-ref/svccat-response-object.rst

.. include:: authentication-ref/user-response-object.rst
