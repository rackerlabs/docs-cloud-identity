.. _reset-phone-pin:

Reset the Support PIN
~~~~~~~~~~~~~~~~~~~~~

.. code::

   POST /v2.0/users/{userId}/RAX-AUTH/phone-pin/reset

Reset the Support PIN for a specific user. Users are not allowed to reset
their own Support PINs by calling this service. If a user tries to
reset their Support PIN, the service returns a 403 HTTP response.

..  note::

    This service is only available to the following roles:

    ``identity:user-admin``: Can reset the Support PIN for all of the users on
    the caller's domain.

    ``identity:user-manage``: Can reset the Support PIN of users in the caller's
    domain who have the identity:user-manage role or below.

A successful reset Support PIN request returns no response body with
``HTTP 204`` status code.

The following table shows the possible response codes for this operation:

.. csv-table::
  :header: Response Code, Name, Description
  :widths: 2, 2, 2

  204, No Content, "The request has been fulfilled."
  400, Bad Request, "The request was invalid."
  401, Unauthorized, "You are not authorized to complete this operation.
  This error can occur if the request is submitted with an invalid
  authentication token."
  403, Forbidden, "Caller does not have an appropriate role."
  404, Not Found, "If the caller does not have authorization to reset the phone
  PIN on the specified user or the user does not exist, a 404 HTTP response
  is returned."
  405, Invalid Method, "The method specified in the request is not valid for
  the resource identified in the request URI."
  409, Conflict, "The request could not be completed due to a conflict with
  the current state of the target resource."
  503, Service Fault, "Service is not available."

Request
-------

The following table shows the header parameters for the reset Support PIN
request:

.. csv-table::
  :header: Name, Type, Description
  :widths: 2, 2, 2

    X-Auth-Token, String *(Required)*, A valid authentication token.

The following table shows the request parameters for the reset Support PIN
request:

.. csv-table::
  :header: Name, Type, Description
  :widths: 2, 2, 2

    ``only_if_missing`` , Boolean *(Optional)*, "If the value of this parameter
    is true and the specified user already has a Support PIN, then the service
    returns a 409 HTTP response without changing the user's Support PIN."
