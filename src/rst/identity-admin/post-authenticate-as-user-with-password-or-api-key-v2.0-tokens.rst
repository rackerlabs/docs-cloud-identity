
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _post-authenticate-as-user-with-password-or-api-key-v2.0-tokens:

Authenticate as user with password or API key
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /v2.0/tokens

Authenticates using either a password or API key and generates an authentication token.

Submit the POST token authentication request to the Identity service endpoint URL with ``v2.0/tokens `` supplied as the path and a payload with either of the following credential types: 

* Password credentials: user name and password
* API Key credentials: user name and API key




You might also need to include either the ``tenantId`` or ``tenantName`` on authentication requests with API key or password credentials. Some services use multi-level authentication, with service-specific credentials in addition to vendor-specific credentials. In such cases, associating a user with a tenant can be a method of passing that additional level of identifying information to the service. Also, if a user account is assigned to multiple tenants, then including the tenant information generates the authentication token for the specified tenant.

If the Identity service returns either of the following messages in response to the initial authentication request, your account uses multi-factor authentication and requires additional steps to complete the authentication process. 

* ``403 Forbidden: User must set up multi-factor.`` (See `Configure multi-factor authentication. <proc_mfa_admin.html#mfa_required>`__
* ``401 Unauthorized: Additional authentication credentials required.`` (See `Authenticate with multi-factor authentication <POST_authenticateWithMultiFactor_v2.0_tokens__Token_Calls.html>`__.)






This table shows the possible response codes for this operation:


+--------------+-------------+----------------------------------------------------------------------+
|Response Code |Name         |Description                                                           |
+==============+=============+======================================================================+
|200           |OK           |Operation completed successfully. See response examples.              |
+--------------+-------------+----------------------------------------------------------------------+
|400           |Bad Request  |Missing required parameters. This error also occurs if you include    |
|              |             |both the tenant name and ID in the request.                           |
+--------------+-------------+----------------------------------------------------------------------+
|401           |Unauthorized |* You are not authorized to complete this operation. * Additional     |
|              |             |authentication credentials required. Submit a second authentication   |
|              |             |request with `multi-factor authentication credentials                 |
|              |             |<POST_authenticateWithMultiFactor_v2.0_tokens__Token_Calls.html>`__.  |
|              |             |requires multi-factor authentication credentials. multi-factor        |
|              |             |authentication passcode and session id to complete the authentication |
|              |             |process. `Authenticate with multi-factor authentication.              |
|              |             |<http://docs.rackspace.com/auth/api/v2.0/auth-client-                 |
|              |             |devguide/content/proc_mfa_auth.html>`__.                              |
+--------------+-------------+----------------------------------------------------------------------+
|403           |User disabled|The request is valid, but you do not have permission to access the    |
|              |             |requested resource. Check with the account administrator to request   |
|              |             |access.                                                               |
+--------------+-------------+----------------------------------------------------------------------+
|404           |Item not     |The requested resource was not found. The subject token in X-Subject- |
|              |found        |Token has expired or is no longer available. Use the POST token       |
|              |             |request to get a new token.                                           |
+--------------+-------------+----------------------------------------------------------------------+
|500           |Service Fault|Service is not available                                              |
+--------------+-------------+----------------------------------------------------------------------+


Request
""""""""""""""""








This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|auth                      |Object *(Required)*      |The auth object provides |
|                          |                         |the credentials for the  |
|                          |                         |authentication request.  |
+--------------------------+-------------------------+-------------------------+
|username                  |String *(Required)*      |This is the user name    |
|                          |                         |that you use to log in   |
|                          |                         |to your Rackspace Cloud  |
|                          |                         |control. ``username``    |
|                          |                         |and ``password`` string  |
|                          |                         |values associated with   |
|                          |                         |the Rackspace Cloud      |
|                          |                         |account. Cannot be       |
|                          |                         |specified with           |
|                          |                         |``APIKeyCredentials`` or |
|                          |                         |``token``. These         |
|                          |                         |credentials are the same |
|                          |                         |ones used to log in by   |
|                          |                         |using the Rackspace      |
|                          |                         |Cloud Control Panel. The |
|                          |                         |password must meet the   |
|                          |                         |following criteria: * At |
|                          |                         |least 1 character long;  |
|                          |                         |no maximum * Can include |
|                          |                         |both uppercase and one   |
|                          |                         |lower case character *   |
|                          |                         |Can include alpha,       |
|                          |                         |numeric, and special     |
|                          |                         |characters * Cannot      |
|                          |                         |begin with or contain a  |
|                          |                         |space * Cannot begin     |
|                          |                         |with a numeric or        |
|                          |                         |special character        |
+--------------------------+-------------------------+-------------------------+
|passwordCredentials       |String *(Optional)*      |A                        |
|                          |                         |``passwordCredentials``  |
|                          |                         |object to specify the    |
|                          |                         |``username`` and         |
|                          |                         |``password`` string      |
|                          |                         |values associated with   |
|                          |                         |the Rackspace Cloud      |
|                          |                         |account. Cannot be       |
|                          |                         |specified with           |
|                          |                         |``APIKeyCredentials`` or |
|                          |                         |``token``.               |
+--------------------------+-------------------------+-------------------------+
|RAX-                      |Object *(Optional)*      |An ``APIKeyCredentials`` |
|KSKEY:APIKeyCredentials   |                         |object to specify the    |
|                          |                         |``username`` and         |
|                          |                         |``apiKey`` string values |
|                          |                         |associated with the      |
|                          |                         |Rackspace Cloud account. |
|                          |                         |Cannot be specified with |
|                          |                         |``passwordCredentials``  |
|                          |                         |or ``token``.            |
+--------------------------+-------------------------+-------------------------+
|apiKey                    |String *(Optional)*      |The API key associated   |
|                          |                         |with the Rackspace Cloud |
|                          |                         |account. You can find    |
|                          |                         |your API key on the      |
|                          |                         |Account Settings page in |
|                          |                         |the Cloud Control panel. |
|                          |                         |After logging in, click  |
|                          |                         |your user ID. Then,      |
|                          |                         |select Account Settings  |
|                          |                         |from the menu.           |
+--------------------------+-------------------------+-------------------------+
|password                  |String *(Optional)*      |This is the password     |
|                          |                         |that you use to log in   |
|                          |                         |to a Rackspace Cloud     |
|                          |                         |account. The password    |
|                          |                         |must meet the following  |
|                          |                         |criteria: * At least 8   |
|                          |                         |characters long; no      |
|                          |                         |maximum * Includes at    |
|                          |                         |least one uppercase and  |
|                          |                         |one lower case character |
|                          |                         |* Can include special    |
|                          |                         |characters * Cannot      |
|                          |                         |begin with a space       |
+--------------------------+-------------------------+-------------------------+
|RAX-AUTH:scope            |String *(Optional)*      |Indicates that the       |
|                          |                         |authentication request   |
|                          |                         |is for a scoped multi-   |
|                          |                         |factor authentication    |
|                          |                         |token that provides      |
|                          |                         |capabilities for a user  |
|                          |                         |to set up and enable     |
|                          |                         |multi-factor             |
|                          |                         |authentication on an     |
|                          |                         |account. Specify the     |
|                          |                         |following value: ``SETUP-|
|                          |                         |MFA``                    |
+--------------------------+-------------------------+-------------------------+
|tenantName                |String *(Optional)*      |Specify the name of the  |
|                          |                         |tenant for the specified |
|                          |                         |user account or token.   |
|                          |                         |Both the ``tenantId``    |
|                          |                         |and ``tenantName``       |
|                          |                         |attributes are optional. |
|                          |                         |However, they cannot be  |
|                          |                         |specified together. If   |
|                          |                         |both attributes are      |
|                          |                         |specified, the server    |
|                          |                         |responds with a ``400``  |
|                          |                         |``Bad Request``.         |
+--------------------------+-------------------------+-------------------------+
|tenantId                  |Uuid *(Optional)*        |The tenant ID. Both the  |
|                          |                         |``tenantId`` and         |
|                          |                         |``tenantName``           |
|                          |                         |attributes are optional, |
|                          |                         |but should not be        |
|                          |                         |specified together. If   |
|                          |                         |both attributes are      |
|                          |                         |specified, the server    |
|                          |                         |responds with a ``400``  |
|                          |                         |``Bad Request``.         |
+--------------------------+-------------------------+-------------------------+





**Example Authenticate as user with password or API key: JSON request**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <auth xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
     xmlns="http://docs.openstack.org/identity/api/v2.0">
     <passwordCredentials username="demoAuthor" password="myPassword01"/>
   </auth>





**Example Authenticate as user with password or API key: JSON request**


.. code::

   {"auth": 
   	{"passwordCredentials": 
   		{"username":"demoAuthor", 
   		  "password":"myPassword01"}
   	}
   }





**Example Authenticate as user with password or API key: JSON request**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <auth>
     <apiKeyCredentials
       xmlns="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"
       username="demoauthor"
       apiKey="aaaaa-bbbbb-ccccc-12345678"/>
     </auth>





**Example Authenticate as user with password or API key: JSON request**


.. code::

   {
       "auth": {
           "RAX-KSKEY:apiKeyCredentials": {
               "username": "demoauthor",
               "apiKey": "aaaaa-bbbbb-ccccc-12345678"
           }
       }
   }





**Example Authenticate as user with password or API key: JSON request**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <auth xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns="http://docs.openstack.org/identity/api/v2.0">
     <passwordCredentials username="demoauthor" password="theUsersPassword" tenantId="1100111"/>
   </auth>





**Example Authenticate as user with password or API key: JSON request**


.. code::

   {
       "auth": {
           "RAX-KSKEY:apiKeyCredentials": {
               "username": "demoauthor",
               "apiKey": "aaaaa-bbbbb-ccccc-12345678"
           },
           "tenantId": "1100111"
       }
   }





**Example Authenticate as user with password or API key: JSON request**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <auth xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
     xmlns="http://docs.openstack.org/identity/api/v2.0">
     <RAX-AUTH:scope="SETUP-MFA"/>
     <passwordCredentials username="demoAuthor" password="myPassword01"/>
   </auth>





**Example Authenticate as user with password or API key: JSON request**


.. code::

   {
       "auth": {
                 "RAX-AUTH:scope": "SETUP-MFA", "passwordCredentials": {
                      "username":"'$USER_ADMIN_USERNAME'"
                      "password":"'$PWD'"
            }
       }
   }





Response
""""""""""""""""





This table shows the body parameters for the response:

+-----------------------+-----------------------+------------------------------+
|Name                   |Type                   |Description                   |
+=======================+=======================+==============================+
|access                 |String *(Required)*    |An ``access`` object that     |
|                       |                       |returns token, user, and      |
|                       |                       |service information upon      |
|                       |                       |successful authentication.    |
+-----------------------+-----------------------+------------------------------+
|token                  |String *(Required)*    |The `token object             |
|                       |                       |<Sample_Request_Response-     |
|                       |                       |d1e64.html#authTokenResp>`__  |
|                       |                       |supplies a scoped             |
|                       |                       |authentication token that can |
|                       |                       |be used to access Rackspace   |
|                       |                       |Cloud services for the        |
|                       |                       |specified tenant.             |
+-----------------------+-----------------------+------------------------------+
|user                   |String *(Required)*    |A `user object                |
|                       |                       |<Sample_Request_Response-     |
|                       |                       |d1e64.html#authUserResp>`__   |
|                       |                       |that returns the following    |
|                       |                       |information about the user,   |
|                       |                       |if available for the account: |
|                       |                       |id, name, assigned roles,     |
|                       |                       |default region, domain, multi-|
|                       |                       |factor authentication status. |
+-----------------------+-----------------------+------------------------------+
|serviceCatalog         |String *(Required)*    |The `service catalog object   |
|                       |                       |<Sample_Request_Response-     |
|                       |                       |d1e64.html#authSvccatResp>`__ |
|                       |                       |provides information about    |
|                       |                       |each service available to the |
|                       |                       |authenticated user along with |
|                       |                       |the service endpoints for API |
|                       |                       |requests.                     |
+-----------------------+-----------------------+------------------------------+







**Example Authenticate as user with password or API key: XML response**


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
       <user id="172157" name="yourUserName" rax-auth:defaultRegion="DFW">
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





**Example Authenticate as user with password or API key: JSON response**


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
               "RAX-AUTH:defaultRegion": "DFW"
           }
       }
   }





**Example Authenticate as user with password or API key: JSON response**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <auth xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
     xmlns="http://docs.openstack.org/identity/api/v2.0">
     <RAX-AUTH:scope="SETUP-MFA"/>
     <passwordCredentials username="demoAuthor" password="myPassword01"/>
   </auth>





**Example Authenticate as user with password or API key: JSON response**


.. code::

   {
       "auth": {
                 "RAX-AUTH:scope": "SETUP-MFA", "passwordCredentials": {
                      "username":"'$USER_ADMIN_USERNAME'"
                      "password":"'$PWD'"
            }
       }
   }




