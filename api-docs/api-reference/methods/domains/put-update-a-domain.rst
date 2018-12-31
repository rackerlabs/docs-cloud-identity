.. _update-a-domain:

Update a domain
~~~~~~~~~~~~~~~

.. code::

   PUT /v2.0/RAX-AUTH/domains/{domainId}

Update properties for a domain.

When you submit the update request, include only the parameter values
that you want to update.

.. note::

   - Owner or managers on account are only allowed to update the
     **sessionInactivityTimeout** attribute using the Update domain API
     operation.


The following table shows the possible response codes for this operation:

.. csv-table::
   :header: Response Code, Name, Description
   :widths: 15 25 60

   200, OK, The request completed successfully.
   400, Bad Request, "The request is missing one or more elements, or the values of some elements are invalid."
   401, Unauthorized, You are not authorized to complete this operation. This error can occur if the request is submitted with an invalid authentication token.
   403, Forbidden, "The request was valid, but the server is refusing to respond because you do not have permission to access the requested resource. Submit a request to your account administrator to determine how to gain access."
   404, Not Found, The requested resource was not found.
   405, Invalid Method, The method specified in the request is not valid for the resource identified in the request URI.
   413, Over Limit, The number of items returned is above the allowed limit.
   415, Bad Media Type, Bad media type. This may result if the wrong media type is used in the API request. Check the content-type and accept headers included in the request.
   503, Service Fault, Service is not available.

Request
-------

The following table shows the header parameters for the update a domain
request:

.. csv-table::
   :header: Name, Type, Description

   X-Auth-Token, String *(Required)*, A valid authentication token.

The following table shows the URI parameters for the update a domain request:

.. csv-table::
   :header: Name, Type, Description

   {domainId}, String, A domain ID.

The following table shows the body parameters for the update a domain request:

.. csv-table::
   :header: Name, Type, Description

   RAX-AUTH:domain, Object *(Required)*, "Object to specify these domain configuration settings: ``sessionInactivityTimeout``"
   RAX-AUTH:domain.\ **sessionInactivityTimeout**,  Duration *(Optional)*, Session inactivity timeout property used across all Rackspace UIs. Value must be of type ISO 8601 Duration.


**Example: Update a domain XML request**

.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <rax-auth:domain sessionInactivityTimeout="PT15M"
         xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
         xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
         xmlns:atom="http://www.w3.org/2005/Atom"
         xmlns:identity="http://docs.openstack.org/identity/api/v2.0">
    </rax-auth:domain>


**Example: Update a domain JSON request**

.. code::

    {
        "RAX-AUTH:domain": {
            "sessionInactivityTimeout": "PT15M"
        }
    }


Response
--------

**Example: Update a domain XML response**

.. code::

   < HTTP/1.1 200 OK
   < vary:  Accept, Accept-Encoding, X-Auth-Token
   < Content-Type: application/xml
   < Content-Length: 148

    <?xml version="1.0" encoding="UTF-8"?>
    <rax-auth:domain id="123" enabled="false" name="domain" description="Domain description"
         sessionInactivityTimeout="PT15M"
         xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
         xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
         xmlns:atom="http://www.w3.org/2005/Atom"
         xmlns:identity="http://docs.openstack.org/identity/api/v2.0">
    </rax-auth:domain>


**Example: Update a domain JSON response**

.. code::

   < HTTP/1.1 200 OK
   < vary:  Accept, Accept-Encoding, X-Auth-Token
   < Content-Type: application/json
   < Content-Length: 148

    {
        "RAX-AUTH:domain": {
            "description": "Domain description",
            "enabled": true,
            "id": "123",
            "name": "domain",
            "sessionInactivityTimeout": "PT15M"
        }
    }
