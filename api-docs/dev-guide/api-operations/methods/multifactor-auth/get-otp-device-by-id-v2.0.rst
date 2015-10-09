.. _get-otp-device-by-id-v2.0:

List the specified OTP device
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /v2.0/users/{userId}/RAX-AUTH/multi-factor/otp-devices/{otpDeviceId}

This operation returns the OTP device associated with the account.

This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |The request succeeded.   |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |The request is missing   |
|                          |                         |one or more elements, or |
|                          |                         |the values of some       |
|                          |                         |elements are invalid.    |
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
|                          |                         |requested resource.      |
|                          |                         |Submit a request to your |
|                          |                         |account administrator to |
|                          |                         |determine how to gain    |
|                          |                         |access.                  |
+--------------------------+-------------------------+-------------------------+
|404                       |Not Found                |The requested resource   |
|                          |                         |was not found.           |
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


Request
""""""""""""""""

This table shows the header and URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|X-Auth-Token              |Header                   |A valid admin            |
|                          |String *(Required)*      |authentication token.    |
+--------------------------+-------------------------+-------------------------+
|{userId}                  |URI                      |The unique, system-      |
|                          |String *(Required)*      |generated user ID for an |
|                          |                         |account.                 |
+--------------------------+-------------------------+-------------------------+
|{otpDeviceId}             |String *(Required)*      |The unique system-       |
|                          |                         |generated ID assigned to |
|                          |                         |the OTP device.          |
+--------------------------+-------------------------+-------------------------+


This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|otpDevice                 |Object                   |Returns the following    |
|                          |                         |information for an OTP   |
|                          |                         |device: ID, name,        |
|                          |                         |verification status.     |
+--------------------------+-------------------------+-------------------------+
|otpDevice.\               |String                   |The unique system-       |
|**id**                    |                         |generated ID assigned to |
|                          |                         |the OTP device.          |
+--------------------------+-------------------------+-------------------------+
|otpDevice.\               |String                   |The unique name assigned |
|**name**                  |                         |to the OTP device.       |
+--------------------------+-------------------------+-------------------------+
|otpDevice.\               |Boolean                  |Indicates whether the    |
|**verified**              |                         |OTP device has been      |
|                          |                         |verified.                |
+--------------------------+-------------------------+-------------------------+



**Example:: Get OTP devices for account HTTP request header: XML**


.. code::

   GET /v2.0/users/e0fb2b4ddb594819b697d0048614c117/RAX-AUTH/multi-factor/otp-devices/6b2834a8bef6461e96ef2322b4c72998 HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/xml
   X-Auth-Token: 83aa159390854e4690e4834e0cfa5f6c
   Content-type: application/xml



**Example:: Get OTP devices for account HTTP request header: JSON**

.. code::

   GET /v2.0/users/e0fb2b4ddb594819b697d0048614c117/RAX-AUTH/multi-factor/otp-devices/6b2834a8bef6461e96ef2322b4c72998 HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/json
   X-Auth-Token: 83aa159390854e4690e4834e0cfa5f6c
   Content-type: application/json





Response
""""""""""""""""

**Example: Get OTP devices for account HTTP response header: XML**


.. code::

   HTTP/1.1 200 OK
   Content-Type: application/xml
   

**Example: Retrieves the specified OTP device response: XML**


.. code::

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <rax-auth:otpDevices 
        xmlns:atom="http://www.w3.org/2005/Atom" 
        xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0" 
        xmlns="http://docs.openstack.org/identity/api/v2.0" 
        xmlns:ns4="http://docs.rackspace.com/identity/api/ext/RAX-KSGRP/v1.0" 
        xmlns:rax-ksqa="http://docs.rackspace.com/identity/api/ext/RAX-KSQA/v1.0" 
        xmlns:os-ksadm="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0" 
        xmlns:rax-kskey="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0" 
        xmlns:os-ksec2="http://docs.openstack.org/identity/api/ext/OS-KSEC2/v1.0">
        <rax-auth:otpDevice verified="true" name="NewOTPDevice" id="6b2834a8bef6461e96ef2322b4c72998"/>
   </rax-auth:otpDevices>
   
   



**Example: Get OTP devices for account HTTP response header: JSON**


.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json
   


**Example: Retrieves the specified OTP device response: JSON**


.. code::

   {
       "RAX-AUTH:otpDevice": {
           "id": "6b2834a8bef6461e96ef2322b4c72998",
           "verified": true,
           "name": "NewOTPDevice"
       }
   }




