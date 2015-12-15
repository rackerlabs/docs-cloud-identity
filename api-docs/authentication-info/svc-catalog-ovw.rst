.. _service-types-in-catalog:

Service types
---------------

The service catalog provides information about Rackspace Cloud services
that are available to customers who have successfully authenticated,
including the API service endpoints to access the service. You can view
:ref:`service catalog details <svccat-resource>` in the
authentication response returned by the Identity service.

Each service has a unique name and an associated service type that
identities the function that the service provides.

.. auth-svccat-types:

Service types in the catalog
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Every service listed in the catalog is associated with a service type.
You can use the service type to identify services that perform similar
functions, whatever those services are named.

The following table provides information about the service types
supported by the Rackspace Cloud. To learn more about any of the
Rackspace services listed, see the `Rackspace developer
documentation`_.

**Table: Service types**

+------------------------+----------------------------------------------------+
| Service type           | Description                                        |
+========================+====================================================+
|`compute`               | Services of this type provide managed VMs and      |
|                        | bare-metal servers in the cloud.                   |
|                        |                                                    |
|                        | Cloud Servers is the name of a Rackspace Cloud     |
|                        | Cloud service of this type. This Rackspace         |
|                        | service is compatible with the                     |
|                        | `OpenStack Compute (Nova) version 1.1 service`_.   |
|                        |                                                    |
+------------------------+----------------------------------------------------+
| `identity`             | Services of this type provide authentication,      |
|                        | authorization, administration, and audit           |
|                        | capabilities to provision and manage users         |
|                        | who request access to Rackspace Cloud service      |
|                        | access to Rackspace Cloud services.                |
|                        |                                                    |
|                        | Cloud Identity is the name of the Rackspace Cloud  |
|                        | service of this type. The Rackspace service is     |
|                        | compatible with the                                |
|                        | `OpenStack Identity (Keystone) version 2 service`_.|
+------------------------+----------------------------------------------------+
| `image`                | Services of this type offer retrieval, storage     |
|                        | storage, and metadata assignment for               |
|                        | Rackspace Cloud Server images.                     |
|                        |                                                    |
|                        | Cloud Images is the name of the Rackspace          |
|                        | Cloud service of this type. The Rackspace          |
|                        | service is compatible with the                     |
|                        | `OpenStack Images (Glance) service`_ .             |
+------------------------+----------------------------------------------------+
| `object-store`         | Services of this type provide scalable cloud       |
|                        | object storage for files and media.                |
|                        |                                                    |
|                        | Cloud Files is the name of the Rackspace Cloud     |
|                        | service of this type. The Rackspace service        |
|                        | is compatible with the                             |
|                        | `OpenStack Object Storage (Swift) service`_.       |
+------------------------+----------------------------------------------------+
| `network`              | Services of this type enable you to create         |
|                        | isolated networks that provision server            |
|                        | instances with Rackspace networks or the           |
|                        | isolated networks you create.                      |
|                        |                                                    |
|                        | Rackspace supports two services of this type:      |
|                        |                                                    |
|                        | -  Cloud Networks, which is compatible with the    |
|                        |    `OpenStack Networking (Neutron) Service`_.      |
|                        |                                                    |
|                        | -  The nova-network component of the               |
|                        |    Rackspace Cloud Servers Service, which          |
|                        |    is compatible with the network component        |
|                        |    of the `OpenStack Compute (Nova) service`_.     |         
+------------------------+----------------------------------------------------+
| `volume`               | Services of this type provide online object        |
|                        | storage for files and allow customers to           |
|                        | mount drives or volumes to their Rackspace         |
|                        | Next Generation Cloud Servers™.                    |
|                        |                                                    |
|                        | Cloud BlockStorage is the name of a Rackspace      |
|                        | Cloud service of this type. The                    |
|                        | Rackspace service is built on the                  |
|                        | `OpenStack Block Storage (Cinder) service`_.       |
+------------------------+----------------------------------------------------+
| `rax:autoscale`        | Services of this type enable you to define         |
|                        | policies to dynamically scale cloud                |
|                        | resources in response to changing                  |
|                        | workloads.                                         |
|                        |                                                    |
|                        | Rackspace Auto Scale is the name of a              |
|                        | Rackspace Cloud service of this type.              |
+------------------------+----------------------------------------------------+
| `rax:backup`           | Services of this type enable you to create         |
|                        | and manage backup versions of cloud server         |
|                        | files and folders that you select, and to          |
|                        | restore files to their original location or        |
|                        | to another server.                                 |
|                        |                                                    |
|                        | Cloud Backup is the name of a Rackspace            |
|                        | Cloud service of this type.                        |
+------------------------+----------------------------------------------------+
| `rax:bigdata`          | Services of this type provide on-demand            |
|                        | Apache Hadoop service available in the             |
|                        | Rackspace Cloud that enable you to deploy,         |
|                        | manage, and scale Hadoop clusters.                 |
|                        |                                                    |
|                        | Cloud Big Data is the name of a Rackspace          |
|                        | Cloud service of this type.                        |
+------------------------+----------------------------------------------------+
| `rax:database`         | Services of this type provide fast,                |
|                        | scalable, fully managed MySQL databases in         |
|                        | the Rackspace Cloud.                               |
|                        |                                                    |
|                        | Cloud Databases is the name of a Rackspace         |
|                        | Cloud service of this type.                        |
+------------------------+----------------------------------------------------+
| `rax:dns`              | Services of this type simplify and automate        |
|                        | DNS management.                                    |
|                        |                                                    |
|                        | Cloud DNS is the name of a Rackspace Cloud         |
|                        | service of this type.                              |
+------------------------+----------------------------------------------------+
| `rax:feeds`            | Services of this type enable customers on          |
|                        | the Rackspace public cloud to access and           |
|                        | collect near real-time usage and system            |
|                        | event data that can be used for analysis,          |
|                        | monitoring, and automation.                        |
|                        |                                                    |
|                        | Cloud Feeds is the name of a Rackspace             |
|                        | Cloud service of this type.                        |
+------------------------+----------------------------------------------------+
| `rax:load-balancer`    | Services of this type provide on-demand,           |
|                        | scalable traffic management.                       |
|                        |                                                    |
|                        | Cloud Load Balancers is the name of a              |
|                        | Rackspace Cloud service of this type.              |
+------------------------+----------------------------------------------------+
| `rax:cloudmetrics`     | Services of this type allow users to               |
|                        | collect and analyze various metrics and to         |
|                        | quickly iterate through the data with              |
|                        | queries and set up dashboard metrics for           |
|                        | ongoing metrics monitoring.                        |
|                        |                                                    |
|                        | Cloud Metrics is the name of a Rackspace           |
|                        | Cloud service of this type.                        |
+------------------------+----------------------------------------------------+
| `rax:monitor`          | Services of this type enable you to create         |
|                        | custom infrastructure monitoring with              |
|                        | real-time alerts, notifications, and               |
|                        | flexible configurations.                           |
|                        |                                                    |
|                        | Cloud Monitoring is the name of a Rackspace        |
|                        | Cloud service of this type.                        |
+------------------------+----------------------------------------------------+
| `rax:orchestration`    | Services of this type enable you to automate and   |
|                        | standardize cloud infrastructure setup and         |
|                        | management.                                        |
|                        |                                                    |
|                        | Cloud Orchestration is the name of the             |
|                        | Rackspace service of this type. The                |
|                        | Rackspace Cloud service is compatible with         |
|                        | the `OpenStack Orchestration (Heat) service`_.     |            
|                        |                                                    |
+------------------------+----------------------------------------------------+
| `rax:queues`           | Services of this type provide an                   |
|                        | open-source, scalable, and highly available        |
|                        | message and notifications service.                 |
|                        |                                                    |
|                        | Cloud Queues is the name of a Rackspace            |
|                        | Cloud service of this type. This service is        |
|                        | like the OpenStack Messages (Zaqar)                |
|                        | service.                                           |
+------------------------+----------------------------------------------------+

.. _Rackspace developer documentation: https://developer.rackspace.com/docs/

.. _OpenStack Compute (Nova) version 1.1 service: http://docs.openstack.org/developer/nova/

.. _OpenStack Identity (Keystone) version 2 service: http://docs.openstack.org/developer/keystone/

.. _OpenStack Images (Glance) service: http://docs.openstack.org/developer/heat/

.. _OpenStack Networking (Neutron) service: http://docs.openstack.org/developer/neutron/

.. _OpenStack Compute (Nova) service: http://docs.openstack.org/developer/nova/

.. _OpenStack Object Storage (Swift) service: http://docs.openstack.org/developer/swift/

.. _OpenStack Block Storage (Cinder) service: http://docs.openstack.org/developer/cinder/ 

.. _OpenStack Orchestration (Heat) service: http://docs.openstack.org/developer/heat/


.. _auth-svccat-workflow:

Suggested work flow for processing a service catalog response
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

When your client issues a successful authentication request, the Cloud
Identity service returns a service catalog that lists the available
services and endpoints to access them. (See 
:ref:`annotated-auth-req-resp` for a service catalog example.)

As the client developer, you must decide how your client can use the
contents of its service catalog. The first step is to identify a service
that you want the client to access. Following is one possible work flow
for processing the service catalog response to identify available
services and their endpoints:

-  If the service catalog lists only one endpoint, use it.

   This endpoint connects your client to the only service available.

-  If the service catalog lists multiple endpoints, establish a process
   for the client to select the endpoint for the connection:

   -  If the user does not specify which endpoint to use, generate an
      error.

   -  If the user specified which endpoint to use, help the user
      identify that endpoint from within the catalog:

      -  Support filtering by endpoint name, service name, service type,
         region name, and version.

      -  Support manual specification of an endpoint via a URL
         parameter.

..  tip:: 

    When you parse an authentication response programmatically, use the
    service `type` instead of service `name` as the basis for
    determining whether a user has access to a particular kind of service.
    Service type is stable across all releases; new service types can be
    added, but existing service types are not renamed. For example, if new
    compute services are added with different names, the service `type`
    filter returns all available services.

 
**Example: Connect a client to an endpoint listed as`type="compute"`.**

#. Navigate to the endpoint for the specified `compute` service, and
   use its `WWW-Authenticate` header to determine what authentication
   server it uses.

#. Go to that authentication server and authenticate.

#. Return to the `compute` endpoint and proceed with using the compute
   service.
   