.. _svccat-resource:

Service catalog resource: Authentication response attributes
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The Service catalog object provides service and endpoint information for
services that you can access with the authentication token returned in
the authentication response.

The information returned for a service is determined by the Identity
service configuration and the tenant and role assignments of the
authenticated user. For example, if a service has an endpoint for
administrative use that endpoint is classified as an AdminURL. The
AdminURL is only visible to authenticated Service administrators (`role =
service:admin`) and Idenity administrators (`role =
identity:admin`).

Responses can be in :ref:`JSON <auth-resp-svccat-resp-json>` or 
:ref:`XML <auth-resp-svccat-resp-xml>`. 
For details, see the table of 
:ref:`service resource object attribute description 
descriptions <auth-resp-svccat-obj-attribs>` following the examples.

.. _auth-resp-svccat-resp-json: 

**Example: Authentication response: Service catalog object in JSON
format**

.. code::  

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
                        },
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
                            "region": "IAD",
                            "tenantId": "123456",
                            "publicURL": "https://iad.databases.api.rackspacecloud.com/v1.0/123456"
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
             ]

            

.. _auth-resp-svccat-resp-xml: 

**Example: Authentication response: Service catalog object in XML
format**

.. code::  

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
             

The user object returns a service object returns the list of services that the user can access. Each service object includes an endpoint object with information about the service region, tenant, and service access 
endpoints.

.. _auth-resp-svccat-obj-attribs: 

**Table: Authentication response: Service catalog object attributes**

+-----------+--------+------------------------------------------------------------------------------------------+
| Attribute | Type   | Description                                                                              |
+===========+========+==========================================================================================+
| `name`    | String | The service name attribute identifies each unique service in the,catalog. Service names  |
|           |        | are defined in the Identity Service configuration,and do not change. However,            |
|           |        | new services of the same service type can be,added to the catalog with new names.        |
|           |        |                                                                                          |
+-----------+--------+------------------------------------------------------------------------------------------+
| `type`    | String | The type of service provided at the specified endpoint,, compute, object-store,          |
|           |        | or rax:loadbalancer for example. Service types categorize the services                   |
|           |        | registered with OpenStack or custom types,registered with the Rackspace                  |
|           |        | Cloud Identity service. For a list of service types, see Service Types,                  |
+-----------+--------+------------------------------------------------------------------------------------------+

.. important:: 
   Use service type as the primary value for locating a service. If multiple endpoints of 
   the same service type exist in the same region, use service name as the tiebreaker. 
   See :ref:`Suggested workflow for processing a Service Catalog <auth-svccat-workflow>`.

.. _auth-resp-svccat-endpoint-obj-attribs: 

**Table: Authentication response: Endpoint catalog object attributes**

+-------------+--------+--------------------------------------------------------------------------------------+
| Attribute   | Type   | Description                                                                          |
+=============+========+======================================================================================+
| `region`    | String | The location of the Rackspace data center where the specified service is hosted.     |
|             |        | Accessing a service from a regional endpoint allows clients to provision resources   |
|             |        | in a manner that provides high availability.                                         |
+-------------+--------+--------------------------------------------------------------------------------------+
| `tenantId`  | String | Some services recognize specification of a tenant. If a service recognizes tenants,  |
|             |        | the format of the tenant specification is defined only by the service. For details   |
|             |        | about whether and how to specify a tenant, check the documentation for the           |
|             |        | service you are using.                                                               |
+-------------+--------+--------------------------------------------------------------------------------------+
|`publicURL`  | URI    | An endpoint can be assigned public, internal, and administrative service URLs.       |
|`internalURL`|        | Access to a public URL usually incurs traffic charges. Internal and admin URLs       |
|`AdminURL`   |        | are accessible only to services within the same region. Access to an internal URL    |
|             |        | is free of charge.                                                                   |
|             |        |                                                                                      |
|             |        | The URL includes the API version and tenant ID for services that require it.         |
|             |        | For example, in thehttps://iad.servers.api.rackspacecloud.com/v2/12345URL,           |
|             |        | the version ID is 2 and the tenant ID is 12345. (The tenant ID is also referred      |
|             |        | to as the account number.)                                                           |
+-------------+--------+--------------------------------------------------------------------------------------+
| `versionId` | String | Specifies the API version for the endpoint. The API version is also included in      |
|             |        | the URL to access the service.                                                       |
+-------------+--------+--------------------------------------------------------------------------------------+
|`versionInfo`| URI    | URI to get information about the specified API version. You can also retrieve        |
|             |        | information about an API version by using the Show version details API operation     |
|             |        | for the specified service--for example, `GET endpointURL// vversion_number`.         |
+-------------+--------+--------------------------------------------------------------------------------------+
|`versionList`| URI    | URI to get information about all versions. You can also retrieve this information    |
|             |        | by using the List versions API operation for the specified service,                  |
|             |        | `GET endpointURL` for example.                                                       |
+-------------+--------+--------------------------------------------------------------------------------------+
