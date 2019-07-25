.. _unlock-phone-pin:

Unlock the Support PIN
~~~~~~~~~~~~~~~~~~~~~~

.. code::

   PUT /v2.0/users/{userId}/RAX-AUTH/phone-pin/unlock

Users can unlock their Support PINs by calling this service.


..  note::

    If users try to unlock a Support PIN for any user apart from themselves,
    the service returns a ``HTTP 403`` response.

    The service also gives an error with code ``HTTP 403`` if a user attempts to
    unlock the their Support PIN when the Support PIN is not in locked state.


The following table shows the possible response codes for this operation:

.. csv-table::
  :header: Response Code, Name, Description
  :widths: 2, 2, 2

  204, No Content, "The request has been fulfilled. The Support PIN is
  unlocked."
  400, Bad Request, "The request was invalid."
  401, Unauthorized, "You are not authorized to complete this operation.
  This error can occur if the request is submitted with an invalid
  authentication token."
  403, Forbidden, "Caller does not have an appropriate role or Support PIN is
  not in a locked state"
  404, Not Found, "The user was not found."
  405, Invalid Method, "The method specified in the request is not valid for
  the resource identified in the request URI."
  503, Service Fault, "Service is not available."

Request
-------

The following table shows the header parameters for the unlock Support PIN
request:

.. csv-table::
  :header: Name, Type, Description
  :widths: 2, 2, 2

  X-Auth-Token, String *(Required)*, A valid authentication token.

.. note::

    There is no request body for this service.

Response
--------

A successful unlock Support PIN request returns no response body with
``HTTP 204`` status code. Response body is only returned in case
service errors.

**Example: When attempt is made to unlock a Support PIN which is
not in locked state JSON response**

.. code::

    {
        "forbidden": {
            "code": 403,
            "message": "User's current Support PIN is not in locked state."
        }
    }

**Example: When invalid user ID is passed in request url JSON response**

.. code::

    {
        "itemNotFound": {
            "code": 404,
            "message": "User 12345 not found"
        }
    }
