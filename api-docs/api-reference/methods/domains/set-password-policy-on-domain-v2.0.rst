.. _set-password-policy-on-domain-v2.0:

Set domain password policy
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    PUT /v2.0/RAX-AUTH/domains/{domainId}/password-policy

Set the domain's password policy. The policy allows authorized users to set a
password rotation requirement for all users within the domain. This forces
users to change their password after a specified time period. A User
administrator can set a policy on their own domain. System and Identity
administrators can set a policy on any domain. A password policy is effective
immediately for a domain.


.. note::

    - If the password on a user's account has been updated since the Identity
      3.12.0 release in June, 2017, Identity uses the date and time
      of the password change to determine whether the password has expired.
      Otherwise, Identity uses the last time any attribute on the account
      was updated (including password, email, and MFA settings).

    - Password policies can only be set using JSON. XML is not supported.

    - Regardless of the value set for ``passwordHistoryRestriction``, a user's
      password cannot be updated to its current password.

The following table shows the possible response codes for this operation:

.. csv-table::
    :header: Response Code, Name, Description
    :widths: 15 25 60

    200, Updated, "The request has been fulfilled. The domain's password
    policy was updated."
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

    {domainId}, String *(Required)*, A domain ID.

The following table shows the body parameters for the request:

.. csv-table::
    :header: Name, Type, Description
    :widths: 2, 2, 2

    passwordPolicy, Object, The password policy
    passwordPolicy.\ **passwordDuration**, String, "The duration for which
    a password can be used. The format is similar to an ISO 8601
    Duration (https://en.wikipedia.org/wiki/ISO_8601#Durations), but
    only days, hours, minutes, and seconds can be specified."
    passwordPolicy.\ **passwordHistoryRestriction**, String *(Optional)*, "An
    integer value from 0-10 specifying how many previous passwords are
    looked at when a new password is being set. A value of ``0`` means the
    password history will be ignored."

**Example: PUT Method request: JSON**

This example demonstrates setting a password policy with a password expiration
time of 90 days, 6 hours, 30 minutes, and 5 seconds after the password was set.

.. code::

    {
        "passwordPolicy": {
            "passwordDuration": "P90DT6H30M5S",
            "passwordHistoryRestriction": "10"
        }
    }

Response
--------

**Example:  PUT Method response: JSON**

.. code::

    {
        "passwordPolicy": {
            "passwordDuration": "P90DT6H30M5S",
            "passwordHistoryRestriction": "10"
        }
    }
