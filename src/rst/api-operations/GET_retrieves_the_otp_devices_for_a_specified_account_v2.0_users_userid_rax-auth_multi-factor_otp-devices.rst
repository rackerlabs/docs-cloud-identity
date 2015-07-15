=============================================================================
Retrieves The Otp Devices For A Specified Account -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Retrieves The Otp Devices For A Specified Account
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_retrieves_the_otp_devices_for_a_specified_account_v2.0_users_userid_rax-auth_multi-factor_otp-devices.rst#request>`__
`Response <GET_retrieves_the_otp_devices_for_a_specified_account_v2.0_users_userid_rax-auth_multi-factor_otp-devices.rst#response>`__

.. code-block:: javascript

    GET /v2.0/users/{userId}/RAX-AUTH/multi-factor/otp-devices

Gets a list of multi-factor OTP devices for an account.

Returns information about the OTP devices associated with a user account.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |The request succeeded.   |
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








**Example Get OTP devices for account: XML request**


.. code::

    GET /v2.0/users/e0fb2b4ddb594819b697d0048614c117/RAX-AUTH/multi-factor/otp-devices HTTP/1.1
    Host: identity.api.rackspacecloud.com
    Accept: application/xml
    X-Auth-Token: 9c069077e4eb438daf8527ba7cc0a7ad
    Content-type: application/xml


**Example Get OTP devices for account: JSON request**


.. code::

    GET /v2.0/users/e0fb2b4ddb594819b697d0048614c117/RAX-AUTH/multi-factor/otp-devices HTTP/1.1
    Host: identity.api.rackspacecloud.com
    Accept: application/json
    X-Auth-Token: 9c069077e4eb438daf8527ba7cc0a7ad
    Content-type: application/json


Response
^^^^^^^^^^^^^^^^^^


This table shows the body parameters for the response:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|otpDevices                |object                   |Returns the collection   |
|                          |                         |of OTP devices           |
|                          |                         |associated with the      |
|                          |                         |specified account.       |
+--------------------------+-------------------------+-------------------------+
|otpDevice                 |object                   |Returns the following    |
|                          |                         |information for an OTP   |
|                          |                         |device: ID, name,        |
|                          |                         |verification status.     |
+--------------------------+-------------------------+-------------------------+





**Example Retrieves The Otp Devices For A Specified Account: XML request**


.. code::

    HTTP/1.1 200 OK
    Content-Type: application/xml
    


**Example Retrieves The Otp Devices For A Specified Account: XML request**


.. code::

    HTTP/1.1 200 OK
    Content-Type: application/xml
    


**Example Retrieves The Otp Devices For A Specified Account: JSON request**


.. code::

    HTTP/1.1 200 OK
    Content-Type: application/json
    

