=============================================================================
Removes A Specified Otp Device From A User Account -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Removes A Specified Otp Device From A User Account
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <DELETE_removes_a_specified_otp_device_from_a_user_account_v2.0_users_userid_rax-auth_multi-factor_otp-devices_otpdeviceid_.rst#request>`__
`Response <DELETE_removes_a_specified_otp_device_from_a_user_account_v2.0_users_userid_rax-auth_multi-factor_otp-devices_otpdeviceid_.rst#response>`__

.. code-block:: javascript

    DELETE /v2.0/users/{userId}/RAX-AUTH/multi-factor/otp-devices/{otpDeviceId}

Delete the OTP device that matches the specified ID.

The operation deletes the OTP device with the specified ID from the user account.



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








**Example Delete OTP device by ID: XML request**


.. code::

    DELETE /v2.0/users/e0fb2b4ddb594819b697d0048614c117/RAX-AUTH/multi-factor/otp-devices/6b2834a8bef6461e96ef2322b4c72998 HTTP/1.1
    Host: identity.api.rackspacecloud.com
    Accept: application/xml
    X-Auth-Token: 83aa159390854e4690e4834e0cfa5f6c
    Content-type: application/xml


**Example Delete OTP device by ID: JSON request**


.. code::

    DELETE /v2.0/users/e0fb2b4ddb594819b697d0048614c117/RAX-AUTH/multi-factor/otp-devices/6b2834a8bef6461e96ef2322b4c72998 HTTP/1.1
    Host: identity.api.rackspacecloud.com
    Accept: application/json
    X-Auth-Token: 83aa159390854e4690e4834e0cfa5f6c
    Content-type: application/json


Response
^^^^^^^^^^^^^^^^^^





**Example Delete device by ID: 204 respone**


.. code::

    HTTP/1.1 204 No Content
    

