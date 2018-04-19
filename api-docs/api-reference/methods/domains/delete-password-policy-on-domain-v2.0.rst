.. _delete-password-policy-on-domain-v2.0:

Delete domain password policy
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    DELETE /v2.0/RAX-AUTH/domains/{domainId}/password-policy

This method deletes the domain's password policy. For more information on password
policies, see :ref:`set-password-policy-on-domain-v2.0`.

The following table shows the possible response codes for this operation:

.. csv-table::
    :header: Response Code, Name, Description
    :widths: 2, 2, 2

    204, No Content, "The request has been fulfilled. The domain's password
    policy was deleted."
    400, Bad Request, "The request is missing one or more elements, or
    the values of some elements are invalid."
    401, Unauthorized, "You are not authorized to complete this operation.
    This error can occur if the request is submitted with an invalid
    authentication token."
    403, Forbidden, "The request was valid, but the server is refusing to
    respond because you do not have permission to access the requested
    resource. Submit a request to your account administrator to
    determine how to gain access."
    404, Not Found, "The requested resource was not found."
    405, Invalid Method, "The method specified in the request is not valid for
    the resource identified in the request URI."
    413, Over Limit, "The number of items returned is above the allowed limit."
    503, Service Fault, "The service is not available."


Request
-------

The following table shows the header parameters for the request:

.. csv-table::
    :header: Name, Type, Description
    :widths: 2, 2, 2

    X-Auth-Token, String *(Required)*, A valid authentication token.

The following table shows the URI parameters for the request:

.. csv-table::
    :header: Name, Type, Description
    :widths: 2, 2, 2

    ``{domainId}``, String *(Required)*, A domain ID.

This operation does not accept a request body.

Response
--------

This operation does not return a response body.
