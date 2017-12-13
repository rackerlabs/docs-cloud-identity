.. _get-list-users-for-tenant-v2.0:

List users for tenant
~~~~~~~~~~~~~~~~~~~~~

.. code::

   GET /v2.0/tenants/{tenantId}/users

Lists all users for a tenant.

.. note::

   - Page query parameters are ignored when using ``contactId`` query parameter.

This table shows the possible response codes for this operation:

.. csv-table::
   :header: Response code, Name, Description
   :widths: auto

   200, OK, The request has been fulfilled. The users for tenant have been retrieved.
   400, Bad Request, "The request is missing one or more elements, or
   the values of some elements are invalid."
   401, Unauthorized, "You are not authorized to complete this operation.
   This error can occur if the request is submitted with an invalid
   authentication token."
   403, Forbidden, "The request was valid, but the server is refusing to
   respond because you do not have permission to access the requested
   resource. Submit a request to your account administrator to
   determine how to gain access."
   404, Not Found, The requested resource was not found.
   405, Invalid Method, "The method specified in the request is not valid for
   the resource identified in the request URI."
   406, Not Acceptable, The server cannot send data in a format requested.
   413, Over Limit, The number of items returned is above the allowed limit.
   503, Service Fault, Service is not available.

Request
-------

This table shows the header parameters for the request:

.. csv-table::
   :header: Name, Type, Description
   :widths: auto

   X-Auth-Token, String *(Required)*, A valid authentication token.


This operation does not accept a request body.

Response
--------

This table shows the URI parameters for the request:

.. csv-table::
   :header: Name, Type, Description
   :widths: auto

   {tenantId}, String, The unique ID assigned to the tenant account.

This table shows the query parameters for the request:

.. csv-table::
   :header: Name, Type, Description
   :widths: auto

   roleId, String *(Optional)*, Filter users with role for tenant. Mutually exclusive with ``contactId`` query parameter.
   contactId, String *(Optional)*, Filter users with contact ID for tenant. Mutually exclusive with ``roleId`` query parameter.
   marker, Object *(Optional)*, Allows us to page through list of users for a tenant. This is the numeric id of the item to start the list.
   limit, Object *(Optional)*, Allows us to set size of page when paging through list of users for a tenant. This is the number of items per page.

Response:

**Example: List users for tenant XML response**

.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <users
          xmlns="http://docs.openstack.org/identity/api/v2.0"
          xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
          xmlns:atom="http://www.w3.org/2005/Atom">
          <user
                email="john.smith@example.org"
                enabled="true" id="123456"
                username="jqsmith"/>

          <user email="mike.turner@example.org"
                enabled="true" id="388493"
                username="miketurner"/>

          <user email="poe.joe@object.org"
                enabled="false"
                id="938439"
                username="poejo"/>
    </users>


**Example: List users for tenant JSON response**

.. code::

    {
      "users": [
        {
          "id": "123456",
          "enabled": true,
          "username": "jqsmith",
          "email": "john.smith@example.org"
        },
        {
          "id": "388493",
          "enabled": true,
          "username": "miketurner",
          "email": "mike.turner@example.org"
        },
        {
          "id": "938439",
          "enabled": false,
          "username": "poejo",
          "email": "poe.joe@object.org"
        }
      ]
