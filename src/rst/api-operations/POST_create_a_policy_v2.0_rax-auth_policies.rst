=============================================================================
Create A Policy -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Create A Policy
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <POST_create_a_policy_v2.0_rax-auth_policies.rst#request>`__
`Response <POST_create_a_policy_v2.0_rax-auth_policies.rst#response>`__

.. code-block:: javascript

    POST /v2.0/RAX-AUTH/policies

Create a policy.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|201                       |Created                  |The request has been     |
|                          |                         |fulfilled. The policy    |
|                          |                         |has been                 |
|                          |                         |created.Location of the  |
|                          |                         |URI of the newly-created |
|                          |                         |policy                   |
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

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|X-Auth-Token              |string *(Required)*      |A valid authentication   |
|                          |                         |token.                   |
+--------------------------+-------------------------+-------------------------+








**Example Create A Policy: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <policy
         blob="{context_is_admin: [[role:admin]],admin_or_owner: [[is_admin:True], [project_id:%(project_id)s]],default: [[rule:admin_or_owner]]}"
         enabled="true" global="false" name="nova policy"
         type="nova-json-policy-format"
         xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
         xmlns:identity="http://docs.openstack.org/identity/api/v2.0" xmlns:ns3="http://www.w3.org/2005/Atom">
         <description>This is policy defined for all users of the nova api</description>
    </policy>
    


**Example Create A Policy: JSON request**


.. code::

    {
      "RAX-AUTH:policy": {
        "blob": "{context_is_admin: [[role:admin]],admin_or_owner: [[is_admin:True], [project_id:%(project_id)s]],default: [[rule:admin_or_owner]]}",
        "enabled": true,
        "description": "This is policy defined for all users of the nova api",
        "name": "nova policy",
        "global": false,
        "type": "nova-json-policy-format"
      }
    }


Response
^^^^^^^^^^^^^^^^^^




