.. _get-password-policy-on-domain-v2.0:

Get domain password policy
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /v2.0/RAX-AUTH/domains/{domainId}/password-policy

Get the domain's password policy. For more information on password policies,
see :ref:`set-password-policy-on-domain-v2.0`.


.. note::

    Password policies can only be returned in JSON.

This table shows the possible response codes for this operation:

.. csv-table::
    :header: Response Code, Name, Description
    :widths: 2, 2, 2

    200, OK, "The request has been fulfilled. The domain's password
    policy was returned."
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
    413, Over Limit, "The number of items returned is above the allowed limit.
    503, Service Fault, Service is not available."


Request
-------

This table shows the header parameters for the request:

.. csv-table::
    :header: Name, Type, Description
    :widths: 2, 2, 2

    X-Auth-Token, String *(Required)*, A valid authentication token.

This table shows the URI parameters for the request:

.. csv-table::
    :header: Name, Type, Description
    :widths: 2, 2, 2

    ``{domainId}``, String *(Required)*, A domain ID.


Response
--------

**Example:  GET Method response: JSON**

.. code::

    {
        "passwordPolicy": {
            "passwordDuration": "P90DT6H30M5S"
        }
    }
