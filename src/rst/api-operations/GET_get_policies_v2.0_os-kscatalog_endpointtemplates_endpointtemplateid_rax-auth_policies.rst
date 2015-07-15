=============================================================================
Get Policies -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Get Policies
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_get_policies_v2.0_os-kscatalog_endpointtemplates_endpointtemplateid_rax-auth_policies.rst#request>`__
`Response <GET_get_policies_v2.0_os-kscatalog_endpointtemplates_endpointtemplateid_rax-auth_policies.rst#response>`__

.. code-block:: javascript

    GET /v2.0/OS-KSCATALOG/endpointTemplates/{endpointTemplateId}/RAX-AUTH/policies

Lists all policies for endpoint template



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
|                          |                         |token                    |
+--------------------------+-------------------------+-------------------------+
|{endpointTemplateId}      |string *(Required)*      |An endpoint template Id  |
+--------------------------+-------------------------+-------------------------+








Response
^^^^^^^^^^^^^^^^^^





**Example Get Policies: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <policies algorithm="if-false-deny"
         xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
         xmlns:identity="http://docs.openstack.org/identity/api/v2.0" xmlns:ns3="http://www.w3.org/2005/Atom">
         <policy enabled="true" global="false" id="2" name="nova policy" type="nova-json-policy-format"/>
         <policy enabled="true" global="false" id="122"
              name="admin policies" type="standard-policy-format"/>
    </policies>
    


**Example Get Policies: JSON request**


.. code::

    {
      "RAX-AUTH:policies": {
        "RAX-AUTH:policy": [
          {
            "id": "2",
            "enabled": true,
            "name": "nova policy",
            "global": false,
            "type": "nova-json-policy-format"
          },
          {
            "id": "122",
            "enabled": true,
            "name": "admin policies",
            "global": false,
            "type": "standard-policy-format"
          }
        ],
        "algorithm": "if-false-deny"
      }
    }

