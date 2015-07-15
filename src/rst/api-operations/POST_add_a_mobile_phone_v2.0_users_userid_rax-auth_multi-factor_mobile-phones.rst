=============================================================================
Add A Mobile Phone -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Add A Mobile Phone
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <POST_add_a_mobile_phone_v2.0_users_userid_rax-auth_multi-factor_mobile-phones.rst#request>`__
`Response <POST_add_a_mobile_phone_v2.0_users_userid_rax-auth_multi-factor_mobile-phones.rst#response>`__

.. code-block:: javascript

    POST /v2.0/users/{userId}/RAX-AUTH/multi-factor/mobile-phones

Adds a mobile phone number to the specified user account to support multi-factor authentication.

The operation updates the specified user account with a phone number for multi-factor authentication. The same phone number can be associated with multiple accounts.

Add mobile phone: cURL request$ curl $AUTH_URL/v2.0/users/$USER_ID/RAX-AUTH/multi-factor/mobile-phones  \-X POST \-H "Content-Type: application/json" \-H "X-Auth-Token: $AUTH_TOKEN"-d '{"RAX-AUTH:mobilePhone": { "number": "+1 210-312-4600" }}' \| python -m json.toolThis example assumes that the endpoint URL, user ID, and authentication token have been exported to these environment variables: ``AUTH_URL, USER_ID``, and ``AUTH_TOKEN``.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|201                       |Success                  |The mobile phone has     |
|                          |                         |been added to the user   |
|                          |                         |account.                 |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |The request is missing   |
|                          |                         |one or more elements, or |
|                          |                         |the values of            |
|                          |                         |someelements are         |
|                          |                         |invalid. For example,    |
|                          |                         |you might get this error |
|                          |                         |if the phone number      |
|                          |                         |format is incorrect.     |
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |You are not authorized   |
|                          |                         |to complete this         |
|                          |                         |operation.               |
+--------------------------+-------------------------+-------------------------+
|403                       |Forbidden                |You do not have          |
|                          |                         |permission to access the |
|                          |                         |requested resource.This  |
|                          |                         |error might be returned  |
|                          |                         |if the user ID is        |
|                          |                         |invalid or if it does    |
|                          |                         |not exist.               |
+--------------------------+-------------------------+-------------------------+
|500                       |Service Fault            |The service is not       |
|                          |                         |available.               |
+--------------------------+-------------------------+-------------------------+


Request
^^^^^^^^^^^^^^^^^

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{userId}                  |string *(Required)*      |The unique, system-      |
|                          |                         |generated user ID for an |
|                          |                         |account.                 |
+--------------------------+-------------------------+-------------------------+
|X-Auth-Token              |string *(Required)*      |A valid authentication   |
|                          |                         |token.                   |
+--------------------------+-------------------------+-------------------------+





This table shows the body parameters for the request:

+------------------------+------------------------+----------------------------+
|Name                    |Type                    |Description                 |
+========================+========================+============================+
|number                  |string *(Required)*     |The phone number for the    |
|                        |                        |mobile phone you want to    |
|                        |                        |add in `E.123 format        |
|                        |                        |<https://www.itu.int/rec/T- |
|                        |                        |REC-E.123-200102-I/en>`__.  |
|                        |                        |+1 235-435-623 or +44 42    |
|                        |                        |1123 4567 for example.      |
+------------------------+------------------------+----------------------------+





**Example Add a mobile phone: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <mobilePhone number="+1 265-894-3489"
         xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
         xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
         xmlns:atom="http://www.w3.org/2005/Atom" xmlns:identity="http://docs.openstack.org/identity/api/v2.0"/>
    


**Example Add mobile phone: JSON request**


.. code::

         
     {
        "RAX-AUTH:mobilePhone": {
        "number": "+1 512-555-1000"
        }
     }
    


Response
^^^^^^^^^^^^^^^^^^


This table shows the body parameters for the response:

+------------------------+------------------------+----------------------------+
|Name                    |Type                    |Description                 |
+========================+========================+============================+
|id                      |string *(Required)*     |The unique, system-         |
|                        |                        |generated ID assigned to    |
|                        |                        |the phone added to the      |
|                        |                        |account.                    |
+------------------------+------------------------+----------------------------+
|verified                |Boolean *(Required)*    |A Boolean value that        |
|                        |                        |indicates whether the phone |
|                        |                        |can be used to authenticate |
|                        |                        |to the Identity service.    |
|                        |                        |Phones can be verified by   |
|                        |                        |using the Send verification |
|                        |                        |code and Verify device      |
|                        |                        |operations.                 |
+------------------------+------------------------+----------------------------+
|number                  |string *(Required)*     |The phone number added to   |
|                        |                        |the user account for use    |
|                        |                        |with multi-factor           |
|                        |                        |authentication services.    |
|                        |                        |`E.123 format               |
|                        |                        |<https://www.itu.int/rec/T- |
|                        |                        |REC-E.123-200102-I/en>`__.  |
|                        |                        |+1 235-435-623 or +44 42    |
|                        |                        |1123 4567 for example.      |
+------------------------+------------------------+----------------------------+





**Example Add a mobile phone: XML response**


.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <mobilePhone id="889a7245f49e4ab789ebaebf91c0f1eb" verified="false" number="+1 265-894-3489"
         xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
         xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
         xmlns:atom="http://www.w3.org/2005/Atom" xmlns:identity="http://docs.openstack.org/identity/api/v2.0"/>
    


**Example Add a moble phone: JSON response**


.. code::

    {
    "RAX-AUTH:otpDevice": {
    "id": "12346",
    "keyUri": "otpauth://totp/Example:alice@google.com?secret\u003dJBSWY3DPEHPK3PXP\u0026issuer\u003dExample",
    "verified": false,
    "qrcode": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAoAAAAKAAQAAAAAktvSOAAADJklEQVR42u3dPXLqMBAAYGVekTJHyFFytHA0juIjpKRg0HP8I68E5Gcmtik+NyAwH51md7WSU/7jKwGBQCAQCAQCgUAgEAgEAoFAIBC4Bpji9T5+dkovw+shpacyPPbf9y/neP8TEAgE7gcuHx57MNz91oPTNx/TsL/5nJ5v/RYIBAJ3AMcp7nUEx+E8AU7XS7z5efDTeDMQCAQ+CDgEbJ8zXjdHd6PfDfdM3wKBQODjgf2bf0P62fXxW5kA85ScAoFA4EOBV9no/JNSPbvpZyAQCNwVrNcCSr4ZktNm+LvFBSAQCFwJbDsqYvXskK6nx9+2dgCBQOBKYEk/p16LyzAMtbXxCuHcnLpWPhAIBG4NhvrY0HrxCeYpfktxPnyb/z1/nY0CgUDgRuCl3HMcE8xY7S9tsd2Sq1apKxAIBO4FVo2veV4LyEvrxdwHW5Xa0hzdAYFA4G5g0/i6DEMxbcxGmyEQCATuCvbhXCz+D8Pnko3m3LaZpWmYgUAgcF9wWgsoe8AvZWkg5Kofy57K8+2VTSAQCNwcfLpuqziVPeBtJ0b8uwMQCAQ+CDh1YqTQ+Bo6Maq1gNdczucBAoHAfcAiNJ0Y5ZobM6ba2rLu+X6nsRYIBAI3AUvAVm07KtX+q+L/OZTa7q+NAoFA4Opg6bUI5f3TErClUExrams532vjBwKBwK3AUwnepuiuHCB2qQ7k+UkxDQgEAjcCl+pZk2/eng/j331dTAMCgcBVwWqx8r09X7q0mXVxU9J3jWRAIBC4ARimuLec6+Nbw2Jl1x4vlu9mo0AgELgJeGsXUrPP6FRvsVw6MYBAIHBHsJ3XUr0L6VKEsHYZ1j2BQCBwL/D69Okci/+5it+qcO6Q7jeSAYFA4Ppg/eyPcnxrKKZdnVkRHoMLBAKBO4LNgyNv9pVNs2V9hMVX6S0QCARuC4YTLUI4l2N0992zkIBAIHAPsBxGHfpgl02UIdj7cTgHBAKBq4ExGw27kI5VnW0RTt+Gc0AgELgFeLUWcC6Nr+HEsC6uFKTfLS4AgUDgGuAfXUAgEAgEAoFAIBAIBAKBQCAQCAQ+MvgfowFRJtozjAcAAAAASUVORK5CYII\u003d",
    "name": "Google Authenticator (iPhone)"
    }
    }

