.. _change-pwd-v2.0:

Change password
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /v2.0/users/RAX-AUTH/change-pwd

This service is used to change a user account's
password without supplying an authentication token by including the current
password instead. If a user's domain uses a password policy to enforce
password rotation and the accounts password has expired, the user must use
this service to update the password to a new value.

.. note::

    The new password must be different from the current password.

This table shows the possible response codes for this operation:

.. csv-table::
    :header: Response Code, Name, Description
    :widths: 2, 2, 2

    204, Updated, "The request has been fulfilled. The account's password
    was updated."
    400, Bad Request, "The request is missing one or more elements, or
    the values of some elements are invalid."
    401, Unauthorized, "You are not authorized to complete this operation.
    This error can occur if the request is submitted with an invalid
    current password."
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

This table shows the body parameters for the request:

.. csv-table::
    :header: Name, Type, Description
    :widths: 2, 2, 2

    RAX-AUTH:changePasswordCredentials, Object, "The change password credentials
    object."
    RAX-AUTH:changePasswordCredentials.\ **username**, String, "The username of
    the user whose password is being changed."
    RAX-AUTH:changePasswordCredentials.\ **password**, String, "The current
    password of the user."
    RAX-AUTH:changePasswordCredentials.\ **newPassword**, String, "The new
    password to set on the user."

**Example: POST Method request: JSON**

This example demonstrates updating the password of a user.

.. code::

    {
        "RAX-AUTH:changePasswordCredentials": {
                "username": "exampleUser",
                "password":"Password1",
                "newPassword":"Password2"
        }
    }


**Example: POST Method request: XML**

This example demonstrates updating the password of a user.

.. code::

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <rax:changePasswordCredentials
        xmlns:rax="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
        username="exampleUser"
        password="Password1"
        newPassword="Password2" />

Response
--------

This operation does not return a response body.
