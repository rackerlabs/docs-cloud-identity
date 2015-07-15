=============================================================================
Get A Policy -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Get A Policy
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_get_a_policy_v2.0_rax-auth_policies_policyid_.rst#request>`__
`Response <GET_get_a_policy_v2.0_rax-auth_policies_policyid_.rst#response>`__

.. code-block:: javascript

    GET /v2.0/RAX-AUTH/policies/{policyId}

Retrieves a policy.



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
|404                       |Not Found                |The requested resource   |
|                          |                         |was not found.           |
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
|{policyId}                |string *(Required)*      |A policy ID              |
+--------------------------+-------------------------+-------------------------+








Response
^^^^^^^^^^^^^^^^^^





**Example Get A Policy: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <policy
         blob="{context_is_admin: [[role:admin]],admin_or_owner: [[is_admin:True], [project_id:%(project_id)s]],default: [[rule:admin_or_owner]]}"
         enabled="true" global="false" id="2" name="nova policy"
         type="nova-json-policy-format"
         xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
         xmlns:identity="http://docs.openstack.org/identity/api/v2.0" xmlns:ns3="http://www.w3.org/2005/Atom">
         <description>This is policy defined for all users of the nova api</description>
    </policy>
    


**Example Get A Policy: JSON request**


.. code::

    {
      "RAX-AUTH:policy": {
        "id": "2",
        "blob": "{context_is_admin: [[role:admin]],admin_or_owner: [[is_admin:True], [project_id:%(project_id)s]],default: [[rule:admin_or_owner]]}",
        "enabled": true,
        "description": "This is policy defined for all users of the nova api",
        "name": "nova policy",
        "global": false,
        "type": "nova-json-policy-format"
      }
    }

