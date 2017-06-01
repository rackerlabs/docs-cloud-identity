.. _post-authenticate-as-user-with-password-or-api-key-v2.0:

Authenticate as user with password or API key
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /v2.0/tokens

Use this operation to authenticate to the Rackspace Cloud by using either a
password or API key and generate an authentication token.

Submit the POST token authentication request to the Identity service endpoint
URL with ``v2.0/tokens`` supplied as the path and a payload with either of
the following credential types:

- Password credentials: user name and password
- API Key credentials: user name and API key

If the Identity service returns either of the following messages in response to
the initial authentication request, your account may require multi-factor
authentication and requires additional steps to complete the authentication
process.

If the Identity service returns a 401 or 403 error in response to
the initial authentication request, your account uses multi-factor
authentication and requires additional steps to complete the authentication
process.

This table shows the possible response codes for this operation:

.. list-table::
  :widths: 20 20 60
  :header-rows: 1

  * - Response Code
    - Name
    - Description
  * - 200
    - OK
    - Operation completed successfully. See response examples.
  * - 400
    - Bad Request
    - Missing required parameters. This error also occurs if you include both
      the tenant name and ID in the request.
  * - 401
    - Unauthorized
    - This error message might indicate any of the following conditions:

      - You supplied incorrect credentials.

      - Additional authentication credentials required. Submit a second
        authentication request with :ref:`multi-factor authentication
        credentials <post-authenticate-with-multi-factor-authentication-\
        passcode-credentials-v2.0>`
  * - 403
    - User disabled/Forbidden
    - The ``User disabled`` message indicates that the request is valid, but
      the user does not have access to the requested resource. Check with the
      account administrator to request access.

      The ``Forbidden`` message might be returned because your account requires
      multi-factor authentication, and the feature has not been set up. See
      :ref:`Request to set up multi-factor authentication on a user account
      <req-mfa-setup-token>`.
  * - 500
    - Service Fault
    - Service is not available

See the following sections for information about parameters and request and
response examples:

.. contents::
   :local:
   :depth: 2

Request
-------

This table shows the query parameters for the request:

.. csv-table::
   :header: Name, Type, Description
   :widths: 2, 2, 2

   apply_rcn_roles, Boolean *(Optional)*, "When true, return any roles and
   endpoints to which the user has access due to RCN roles. Defaults to false."

This table shows the body parameters for the request:

.. list-table::
  :widths: 30 20 50
  :header-rows: 1

  * - Name
    - Type
    - Description
  * - auth
    - Object *(Required)*
    - The auth object provides the credentials for the authentication request.
  * - auth.\ **RAX-AUTH:scope**
    - Object *(Optional)*
    - Indicates that the authentication request is for a scoped multi-factor
      authentication token that provides capabilities for a user to set up and
      enable multi-factor authentication on an account. Specify the following
      value: ``SETUP-MFA``. For details, see :ref:`Request mfa setup token \
      <req-mfa-setup-token>`.
  * - auth.\ **passwordCredentials**
    - Object *(Required)*
    - Provides username and password credentials to access the Rackspace Cloud
      account.
  * - auth.passwordCredentials.\ **username**
    - String *(Required)*
    - The user name for the Rackspace Cloud account.
  * - auth.passwordCredentials.\ **tenantId**
    - UUID *(Optional)*
    - The tenant ID for the Rackspace Cloud account. Both the ``tenantId`` and
      ``tenantName`` attributes are optional, but should not be specified
      together.
  * - auth.passwordCredentials.\ **tenantName**
    - String *(Optional)*
    - The tenant name for the Rackspace Cloud account. Both the ``tenantName``
      and ``tenantId`` attributes are optional, but should not be specified
      together.
  * - auth.RAX-KSKEY:\ **APIKeyCredentials**
    - Object *(Required)*
    - Provides username and API key credentials for the authentication request.
  * - auth.RAX-KSKEY:apiKeyCredentials.\ **username**
    - String *(Required)*
    - The user name for the Rackspace Cloud account
  * - auth.RAX-KSKEY:apiKeyCredentials.\ **apiKey**
    - String *(Optional)*
    - The API key associated with the Rackspace Cloud account. You can find
      your API key on the Account Settings page in the Cloud Control panel.
      See :ref:`Get credentials <get-credentials>`.
  * - auth.RAX-KSKEY:apiKeyCredentials.\ **tenantId**
    - UUID *(Optional)*
    - The tenant ID for the Rackspace Cloud account. Both the ``tenantId`` and
      ``tenantName`` attributes are optional, but should not be specified
      together.
  * - auth.RAX-KSKEY:apiKeyCredentials.\ **tenantName**
    - String *(Optional)*
    - The tenant name for the Rackspace Cloud account. Both the ``tenantName``
      and ``tenantId`` attributes are optional, but should not be specified
      together.

Example: Authenticate as user with password XML request
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <auth RAX-AUTH:scope="SETUP-MFA"
     xmlns="http://docs.openstack.org/identity/api/v2.0"
     xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
     xmlns:RAX-AUTH="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
     xmlns:atom="http://www.w3.org/2005/Atom">
     <passwordCredentials password="myPassword01" username="demoauthor"/>
   </auth>

**Example: Authenticate as user with password JSON request**

.. code::

   {
      "auth": {
          "passwordCredentials": {
             "username":"demoAuthor",
             "password":"myPassword01"
          }
       }
   }


**Example: Authenticate as user with API key XML request**

.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <auth>
     <apiKeyCredentials
       xmlns="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"
       username="demoauthor"
       apiKey="aaaaa-bbbbb-ccccc-12345678"/>
     </auth>


Example: Authenticate as user with API key JSON request
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   {
        "auth": {
           "RAX-KSKEY:apiKeyCredentials": {
               "username": "demoauthor",
               "apiKey": "aaaaa-bbbbb-ccccc-12345678"
           }
       }
   }


Example: Authenticate as user with password and tenant Id XML request
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <auth xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns="http://docs.openstack.org/identity/api/v2.0">
     <passwordCredentials username="demoauthor" password="theUsersPassword" tenantId="1100111"/>
   </auth>



Example: Authenticate as user with API key and tenant ID JSON request
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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


Example: Authenticate for multi-factor authentication setup XML request
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <auth xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
     xmlns="http://docs.openstack.org/identity/api/v2.0">
     <RAX-AUTH:scope="SETUP-MFA"/>
     <passwordCredentials username="demoAuthor" password="myPassword01"/>
   </auth>


Example: Authenticate for multi-factor authentication setup JSON request
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
--------

This table shows the body parameters for the response:

+-----------------------+-----------------------+------------------------------+
|Name                   |Type                   |Description                   |
+=======================+=======================+==============================+
|access                 |String *(Required)*    |An ``access`` object that     |
|                       |                       |returns token, user, and      |
|                       |                       |service information upon      |
|                       |                       |successful authentication.    |
+-----------------------+-----------------------+------------------------------+
|token                  |String *(Required)*    |The :ref:`token object        |
|                       |                       |<auth-resp-token-resource>`   |
|                       |                       |supplies a scoped             |
|                       |                       |authentication token that can |
|                       |                       |be used to access Rackspace   |
|                       |                       |Cloud services for the        |
|                       |                       |specified tenant.             |
+-----------------------+-----------------------+------------------------------+
|user                   |String *(Required)*    |A :ref:`user object           |
|                       |                       |<auth-resp-user-resource>`    |
|                       |                       |that returns the following    |
|                       |                       |information about the user,   |
|                       |                       |if available for the account: |
|                       |                       |id, name, assigned roles,     |
|                       |                       |default region, and domain.   |
+-----------------------+-----------------------+------------------------------+
|serviceCatalog         |String *(Required)*    |The :ref:`service catalog     |
|                       |                       |<svccat-resource>`            |
|                       |                       |provides information about    |
|                       |                       |each service available to the |
|                       |                       |authenticated user along with |
|                       |                       |the service endpoints for API |
|                       |                       |requests.                     |
+-----------------------+-----------------------+------------------------------+


Example: Authenticate as user with API key XML response
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
       <user id="172157" name="yourUserName" rax-auth:defaultRegion="DFW" rax-auth:domainId="123456">
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

Example: Authenticate as user with API key JSON response
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^


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
               "RAX-AUTH:domainId": "123456"
           }
       }
   }

Example: Authenticate for multi-factor authentication setup JSON response
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

   .. code::

      {
         "token": {
             "RAX-AUTH:authenticatedBy": [
               "password"
             ],
             "expires": "2014-01-09T15:08:53.645-06:00",
             "id": "449f04aca3594ce38e5b0b18fce6b"
          }
     }

   .. note::

      Use the mfa-setup token returned in the response to set up
      multi-factor authentication on your account. For instructions,
      see :ref:`Multifactor authentication <multifactor-authenication-ovw>`.
