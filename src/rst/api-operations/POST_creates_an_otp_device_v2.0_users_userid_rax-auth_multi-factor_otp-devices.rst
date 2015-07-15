=============================================================================
Creates An Otp Device -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Creates An Otp Device
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <POST_creates_an_otp_device_v2.0_users_userid_rax-auth_multi-factor_otp-devices.rst#request>`__
`Response <POST_creates_an_otp_device_v2.0_users_userid_rax-auth_multi-factor_otp-devices.rst#response>`__

.. code-block:: javascript

    POST /v2.0/users/{userId}/RAX-AUTH/multi-factor/otp-devices

adds a OTP (one-time password) device for multi-factor authentication

You can add up to five OTP devices to a user account. After adding the device, use the `verify OTP device <POST_verifyOTPDevice_v2.0_users__userId__RAX-AUTH_multi-factor_otp-devices__otpDeviceId__verify_Multifactor_Calls.html>`__ operation to pair the device with your account.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|201                       |Success                  |The OTP device has been  |
|                          |                         |added to the user        |
|                          |                         |account.                 |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |The request is missing   |
|                          |                         |one or more elements, or |
|                          |                         |the values of            |
|                          |                         |someelements are invalid.|
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |You are not authorized   |
|                          |                         |to complete this         |
|                          |                         |operation.               |
+--------------------------+-------------------------+-------------------------+
|500                       |Service Fault            |Service is not available.|
+--------------------------+-------------------------+-------------------------+


Request
^^^^^^^^^^^^^^^^^

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{userId}                  |xsd:string *(Required)*  |The unique, system-      |
|                          |                         |generated user ID for an |
|                          |                         |account.                 |
+--------------------------+-------------------------+-------------------------+
|X-Auth-Token              |xsd:string *(Required)*  |A valid authentication   |
|                          |                         |token                    |
+--------------------------+-------------------------+-------------------------+








**Example Add an OTP device: XML request**


.. code::

    POST /v2.0/users/e0fb2b4ddb594819b697d0048614c117/RAX-AUTH/multi-factor/otp-devices HTTP/1.1
    Host: staging.identity-internal.api.rackspacecloud.com
    Accept: application/xml
    X-Auth-Token: 83aa159390854e4690e4834e0cfa1234
    Content-type: application/xml


**Example Add an OTP device: JSON request**


.. code::

    POST /v2.0/users/e0fb2b4ddb594819b697d0048614c117/RAX-AUTH/multi-factor/otp-devices HTTP/1.1
    Host: staging.identity-internal.api.rackspacecloud.com
    Accept: application/json
    X-Auth-Token: 83aa159390854e4690e4834e0cfa1234
    Content-type: application/json


Response
^^^^^^^^^^^^^^^^^^


This table shows the body parameters for the response:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|id                        |string                   |The unique, system-      |
|                          |                         |generated ID assigned to |
|                          |                         |the OTP device.          |
+--------------------------+-------------------------+-------------------------+
|keyUri                    |                         |The URI for the device   |
|                          |                         |security token.          |
+--------------------------+-------------------------+-------------------------+
|name                      |string                   |The unique name assigned |
|                          |                         |to the OTP device.       |
+--------------------------+-------------------------+-------------------------+
|qrcode                    |string                   |The bar code to identity |
|                          |                         |the OTP device to the    |
|                          |                         |mobile passcode          |
|                          |                         |application.             |
+--------------------------+-------------------------+-------------------------+
|verified                  |Boolean                  |Indicates whether the    |
|                          |                         |OTP device has been      |
|                          |                         |verified.                |
+--------------------------+-------------------------+-------------------------+





**Example Add an OTP device: XML response**


.. code::

    POST /v2.0/users/e0fb2b4ddb594819b697d0048614c117/RAX-AUTH/multi-factor/otp-devices HTTP/1.1
    Host: identity.api.rackspacecloud.com
    Accept: application/json
    X-Auth-Token: 83aa159390854e4690e4834e0cfa5f6c
    Content-type: application/json


**Example Add a moble phone: JSON response**


.. code::

    HTTP/1.1 200 OK
    Content-Length: 1985
    Content-Type: application/json
    LOCATION: http://identity.api.rackspacecloud.com/cloud/v2.0/users/e0fb2b4ddb594819b697d0048614c117/RAX-AUTH/multi-factor/otp-devices/a34b5e4a1ffe4514a8859716136dc7cb
    Date: Tue, 05 May 2015 14:09:02 GMT

