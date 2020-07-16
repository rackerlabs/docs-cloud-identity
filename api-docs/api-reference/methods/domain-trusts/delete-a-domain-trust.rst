.. _delete-a-domain-trust:

Delete a domain trust
~~~~~~~~~~~~~~~~~~~~~

.. code::

    DELETE /v2.0/RAX-AUTH/trusts/{domainTrustId}

Use this operation to delete a specified domain trust by domain trust ID.

..  note::

    - A user-admin and user-manage can delete a trust if their domain matches
      the principal domain on the trust.
    - Users with the role ``identity:domain-trust-admin`` can delete any domain
      trust.
    - Use the RAX-AUTH API extension to the Core Identity API to implement this
      API operation

The following table shows the possible response codes for this operation:

.. csv-table::
   :header: Response code, Name, Description
   :widths: auto

    204, No Content, The request has been fulfilled.
    400, Bad Request, The request was invalid.
    401, Unauthorized, "You are not authorized to complete this, operation. This error can occur if the, request is submitted with an invalid, authentication token."
    403, Forbidden, Caller does not have an appropriate role.
    404, Not Found, The requested resource was not found.
    405, Invalid Method, The method specified in the request is not valid for the resource identified in the request URI.
    503, Service Fault, Service is not available.

-------
Request
-------

The following table shows the header parameters for the delete domain trust
request:

.. csv-table::
   :header: Name, Type, Description
   :widths: auto

    X-Auth-Token, String *(Required)*, A valid authentication token.

The following table shows the URI parameters for the delete domain trust
request:

.. csv-table::
   :header: Name, Type, Description
   :widths: auto

    {domainTrustId}, String, A domain trust ID.

**Example: Delete a domain trust: JSON request**

.. code::

    DELETE /v2.0/RAX-AUTH/trusts/123456
    Host: identity.api.rackspacecloud.com
    Accept: application/json
    Content-type: application/json
    X-Auth-Token: c6f56a1d89274da4b14c1de36c412345

--------
Response
--------
This operation does not return a response body.
