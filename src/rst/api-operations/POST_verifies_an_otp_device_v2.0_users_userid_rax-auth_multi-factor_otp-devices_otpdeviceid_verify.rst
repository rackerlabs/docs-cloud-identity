=============================================================================
Verifies An Otp Device -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Verifies An Otp Device
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <POST_verifies_an_otp_device_v2.0_users_userid_rax-auth_multi-factor_otp-devices_otpdeviceid_verify.rst#request>`__
`Response <POST_verifies_an_otp_device_v2.0_users_userid_rax-auth_multi-factor_otp-devices_otpdeviceid_verify.rst#response>`__

.. code-block:: javascript

    POST /v2.0/users/{userId}/RAX-AUTH/multi-factor/otp-devices/{otpDeviceId}/verify

Sends the mobile passcode from the mobile passcode application to the Identity service to pair the OTP device instance with the account.

After you `set up an OTP device for multi-factor authentication <proc_mfa_setup-OTP.html>`__, this operation sends the passcode from the mobile passcode application to the Identity service to confirm that you have the device so that you can use the device for multi-factor authentication.

If your account is set up for multi-factor authentication by using a mobile phone, or if this is the first OTP device on your account, `update the multi-factor authentication settings <PUT_updateMultifactorSettings_v2.0_users__userId__RAX-AUTH_multi-factor_Multifactor_Calls.html>`__ on your account to use the OTP device.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|204                       |No content               |The request succeeded.   |
|                          |                         |The server fulfilled the |
|                          |                         |request but does not     |
|                          |                         |need to return a body.   |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |The request is missing   |
|                          |                         |one or more elements, or |
|                          |                         |the values of            |
|                          |                         |someelements are invalid.|
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |You are not authorized   |
|                          |                         |to complete this         |
|                          |                         |operation. This error    |
|                          |                         |can occur if the request |
|                          |                         |is submitted with an     |
|                          |                         |invalid authentication   |
|                          |                         |token.                   |
+--------------------------+-------------------------+-------------------------+
|403                       |Forbidden                |The request was valid,   |
|                          |                         |but the server is        |
|                          |                         |refusing to respond      |
|                          |                         |because you do not have  |
|                          |                         |permission to access the |
|                          |                         |requested                |
|                          |                         |resource.Submit a        |
|                          |                         |request to your account  |
|                          |                         |administrator to         |
|                          |                         |determine how to gain    |
|                          |                         |access.                  |
+--------------------------+-------------------------+-------------------------+
|405                       |Invalid Method           |The method specified in  |
|                          |                         |the request is not valid |
|                          |                         |for the resource         |
|                          |                         |identified in the        |
|                          |                         |request URI.             |
+--------------------------+-------------------------+-------------------------+
|413                       |Over Limit               |The number of items      |
|                          |                         |returned is above the    |
|                          |                         |allowed limit.           |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Fault            |Service is not available.|
+--------------------------+-------------------------+-------------------------+
|404                       |Not Found                |The requested resource   |
|                          |                         |was not found.           |
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
|{otpDeviceId}             |xsd:string *(Required)*  |The unique system-       |
|                          |                         |generated ID assigned to |
|                          |                         |the OTP device.          |
+--------------------------+-------------------------+-------------------------+





This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|verified                  |Boolean *(Required)*     |Indicates whether the    |
|                          |                         |OTP device has been      |
|                          |                         |verified.                |
+--------------------------+-------------------------+-------------------------+





**Example Verify OTP devices for account: XML request**


.. code::

    POST /v2.0/users/e0fb2b4ddb594819b697d0048614c117/RAX-AUTH/multi-factor/otp-devices/12345e4a1ffe4514a8859716136dc7cb/verify HTTP/1.1
    Host: identity.api.rackspacecloud.com
    Accept: application/json
    X-Auth-Token: 83aa159390854e4690e4834e0c123456
    Content-type: application/json
    
    <?xml version="1.0" encoding="UTF-8"?>
    <verificationCode code="123456"
         xmlns:RAX-AUTH="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
         xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
         xmlns:atom="http://www.w3.org/2005/Atom" xmlns:identity="http://docs.openstack.org/identity/api/v2.0"/>


**Example Verify OTP devices for account: JSON request**


.. code::

    POST /v2.0/users/e0fb2b4ddb594819b697d0048614c117/RAX-AUTH/multi-factor/otp-devices/a34b5e4a1ffe4514a8859716136dc7cb/verify HTTP/1.1
    Host: identity.api.rackspacecloud.com
    Accept: application/json
    X-Auth-Token: 83aa159390854e4690e4834e0cfa5f6c
    Content-type: application/json
    
    {"RAX-AUTH:verificationCode": { "code": "662262" }}


Response
^^^^^^^^^^^^^^^^^^





**Example Verify device by ID: 204 response**


.. code::

    HTTP/1.1 204 No Content
    

