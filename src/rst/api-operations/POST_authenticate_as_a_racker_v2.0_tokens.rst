=============================================================================
Authenticate As A Racker -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Authenticate As A Racker
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <POST_authenticate_as_a_racker_v2.0_tokens.rst#request>`__
`Response <POST_authenticate_as_a_racker_v2.0_tokens.rst#response>`__

.. code-block:: javascript

    POST /v2.0/tokens

Authenticate using Racker credentials.

Rackers can use the ``POST tokens`` operation to authenticate to the Identity service by supplying the following information in the request: Rackspace username, SSO password, and the Rackspace domain ID.

When you authenticate, the Identity service validates the authentication request through the internal Rackspace eDirectory (eDir) service, maps your Racker credentials to the Identity service roles and permissions, and returns an authentication response with a token granting the corresponding access rights and permissions.

User, group, and role configuration for Racker accounts is managed through the eDir service. You can view, manage, and submit eDir service requests by using either of these resources: View and manage your Racker account credentials and submit service requests by using `RackerApp <https://rackerapp.rackspace.com:8443/IDMProv/portal/cn/GuestContainerPage/Welcome>`__. For access and permission requests, submit a ticket from the `Access and Permissions <https://rackspace.service-now.com/ess/sd_order_rack_group.do>`__ section of the Rackspace Service Desk portal.

NotesWhen you are authenticated as a Racker, you cannot create sub-user accounts because your account is not associated with a tenant.

Racker accounts do not use identity roles such as ``identity:admin``, ``identity:default``, ``identity:user-admin``, and ``identity:user-manage.`` Racker account groups and permissions are managed through eDir groups and mapped to Identity roles during the authentication process.

You cannot manage RBAC roles by using the role operations available in the Identity service API. To add or change role assignments, submit a request through RackerApp or the Rackspace Service Desk.

If you use the same account to access the Rackspace Cloud staging environment and production systems, problems in the staging environment might cause failures in production. For example, if your Racker account gets locked out in the staging environment, any production processes that use the same account will fail on authentication. To prevent issues like this, use different accounts in staging and production.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |The request succeeded.   |
+--------------------------+-------------------------+-------------------------+
|409                       |Conflict                 |The request could not be |
|                          |                         |completed due to a       |
|                          |                         |conflict with the        |
|                          |                         |current state of the     |
|                          |                         |resource.                |
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






This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|RAX:AUTH:domain           |string *(Required)*      |Specify the Rackspace    |
|                          |                         |domain name.             |
|                          |                         |``name="Rackspace"``.    |
+--------------------------+-------------------------+-------------------------+





**Example Racker SSO authentication request: XML**


.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <auth xmlns="http://docs.openstack.org/identity/api/v2.0"
         xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
         xmlns:RAX-AUTH="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0" 
         xmlns:atom="http://www.w3.org/2005/Atom">
         <passwordCredentials password="mypassword" username="jqsmith"/>
         <RAX-AUTH:domain name="Rackspace"/>
    </auth>


**Example Racker SSO authentication request: JSON**


.. code::

    {
      "auth": {
        "RAX-AUTH:domain": {
          "name": "Rackspace"
        },
        "passwordCredentials": {
          "username": "jqsmith",
          "password": "mypassword"
        }
      }
    }


**Example Racker RSA token authentication request: XML**


.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <auth xmlns="http://docs.openstack.org/identity/api/v2.0"
         xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
         xmlns:RAX-AUTH="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0" 
         xmlns:atom="http://www.w3.org/2005/Atom">
         <RAX-AUTH:rsaCredentials tokenKey="8723984574" username="jqsmith"/>
         <RAX-AUTH:domain name="Rackspace"/>
    </auth>


**Example Racker RSA token authentication request: JSON**


.. code::

    {
      "auth": {
        "RAX-AUTH:domain": {
          "name": "Rackspace"
        },
        "RAX-AUTH:rsaCredentials": {
          "tokenKey": "8723984574",
          "username": "jqsmith"
        }
      }
    }


Response
^^^^^^^^^^^^^^^^^^





**Example Authenticate As A Racker: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <access xmlns="http://docs.openstack.org/identity/api/v2.0"
         xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0" 
         xmlns:atom="http://www.w3.org/2005/Atom">
         <token expires="2012-04-13T08:15:00.000-05:00" id="aaaaa-bbbbb-ccccc-dddd"/>
         <user name="jqsmith">
              <roles>
                   <role name="Racker"/>
                   <role name="UVC_ServiceUsers"/>
                   <role name="Support"/>
              </roles>
         </user>
    </access>


**Example Authenticate As A Racker: JSON request**


.. code::

    {
      "access": {
        "token": {
          "id": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
          "expires": "2012-04-13T08:15:00.000-05:00"
        },
        "user": {
          "roles": [
            {
              "name": "Racker"
            },
            {
              "name": "UVC_ServiceUsers"
            },
            {
              "name": "Support"
            }
          ],
          "name": "jqsmith"
        }
      }
    }

