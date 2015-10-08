.. _post-creates-an-otp-device-v2.0:

Creates an OTP device
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /v2.0/users/{userId}/RAX-AUTH/multi-factor/otp-devices

adds a OTP (one-time password) device for multi-factor authentication

You can add up to five OTP devices to a user account. After adding the device, 
use the :ref:`verify OTP device <post-verifies-an-otp-device-v2.0>`.


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
|                          |                         |the values of some       |
|                          |                         |elements are invalid.    |
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |You are not authorized   |
|                          |                         |to complete this         |
|                          |                         |operation.               |
+--------------------------+-------------------------+-------------------------+
|500                       |Service Fault            |Service is not available.|
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

This operation does not accept a request body.


**Example:  Add an OTP device HTTP request header: XML**

.. code::

   POST /v2.0/users/e0fb2b4ddb594819b697d0048614c117/RAX-AUTH/multi-factor/otp-devices HTTP/1.1
   Host: staging.identity-internal.api.rackspacecloud.com
   Accept: application/xml
   X-Auth-Token: 83aa159390854e4690e4834e0cfa1234
   Content-type: application/xml


**Example:  Add an OTP device request: XML**

.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <otpDevice name="NewOTPDevice"
        xmlns:RAX-AUTH="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
        xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
        xmlns:atom="http://www.w3.org/2005/Atom" xmlns:identity="http://docs.openstack.org/identity/api/v2.0"/>
   

**Example:  Add an OTP device HTTP request header: JSON**

.. code::

   POST /v2.0/users/e0fb2b4ddb594819b697d0048614c117/RAX-AUTH/multi-factor/otp-devices HTTP/1.1
   Host: staging.identity-internal.api.rackspacecloud.com
   Accept: application/json
   X-Auth-Token: 83aa159390854e4690e4834e0cfa1234
   Content-type: application/json


**Example:  Add an OTP device request: JSON**

.. code::

   {
       "RAX-AUTH:otpDevice": {
   
           "name": "NewOTPDevice"
       
       }
   }

Response
""""""""""""""""

This table shows the header parameters for the response:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|Location                  |Anyuri *(Required)*      |URI for the newly        |
|                          |                         |created OTP device.      |
+--------------------------+-------------------------+-------------------------+


This table shows the body parameters for the response:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|id                        |String                   |The unique, system-      |
|                          |                         |generated ID assigned to |
|                          |                         |the OTP device.          |
+--------------------------+-------------------------+-------------------------+
|keyUri                    |String                   |The URI for the device   |
|                          |                         |security token.          |
+--------------------------+-------------------------+-------------------------+
|name                      |String                   |The unique name assigned |
|                          |                         |to the OTP device.       |
+--------------------------+-------------------------+-------------------------+
|qrcode                    |String                   |The bar code to identity |
|                          |                         |the OTP device to the    |
|                          |                         |mobile passcode          |
|                          |                         |application.             |
+--------------------------+-------------------------+-------------------------+
|verified                  |Boolean                  |Indicates whether the    |
|                          |                         |OTP device has been      |
|                          |                         |verified.                |
+--------------------------+-------------------------+-------------------------+

**Example:  Add an OTP device HTTP response header: XML**

.. code::

   POST /v2.0/users/e0fb2b4ddb594819b697d0048614c117/RAX-AUTH/multi-factor/otp-devices HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/json
   X-Auth-Token: 83aa159390854e4690e4834e0cfa5f6c
   Content-type: application/json


**Example:  Add an OTP device response: XML**


.. code::

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <rax-auth:otpDevice
        xmlns:atom="http://www.w3.org/2005/Atom"
        xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
        xmlns="http://docs.openstack.org/identity/api/v2.0"
        xmlns:ns4="http://docs.rackspace.com/identity/api/ext/RAX-KSGRP/v1.0"
        xmlns:rax-ksqa="http://docs.rackspace.com/identity/api/ext/RAX-KSQA/v1.0"
        xmlns:os-ksadm="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
        xmlns:rax-kskey="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"
        xmlns:os-ksec2="http://docs.openstack.org/identity/api/ext/OS-KSEC2/v1.0">
        <rax-auth:otpDevice
             id="6b2834a8bef6461e96ef2322b4c72998" 
             keyUri="otpauth://totp/Example:alice@google.com?secret\u003dJBSWY3DPEHPK3PXP\u0026issuer\u003dExample"
             qrcode="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAoAAAAKAAQAAAAAktvSOAAADJklEQVR42u3dPXLqMBAAYGVekTJHyFFytHA0juIjpKRg0HP8I68E5Gcmtik+NyAwH51md7WSU/7jKwGBQCAQCAQCgUAgEAgEAoFAIBC4Bpji9T5+dkovw+shpacyPPbf9y/neP8TEAgE7gcuHx57MNz91oPTNx/TsL/5nJ5v/RYIBAJ3AMcp7nUEx+E8AU7XS7z5efDTeDMQCAQ+CDgEbJ8zXjdHd6PfDfdM3wKBQODjgf2bf0P62fXxW5kA85ScAoFA4EOBV9no/JNSPbvpZyAQCNwVrNcCSr4ZktNm+LvFBSAQCFwJbDsqYvXskK6nx9+2dgCBQOBKYEk/p16LyzAMtbXxCuHcnLpWPhAIBG4NhvrY0HrxCeYpfktxPnyb/z1/nY0CgUDgRuCl3HMcE8xY7S9tsd2Sq1apKxAIBO4FVo2veV4LyEvrxdwHW5Xa0hzdAYFA4G5g0/i6DEMxbcxGmyEQCATuCvbhXCz+D8Pnko3m3LaZpWmYgUAgcF9wWgsoe8AvZWkg5Kofy57K8+2VTSAQCNwcfLpuqziVPeBtJ0b8uwMQCAQ+CDh1YqTQ+Bo6Maq1gNdczucBAoHAfcAiNJ0Y5ZobM6ba2rLu+X6nsRYIBAI3AUvAVm07KtX+q+L/OZTa7q+NAoFA4Opg6bUI5f3TErClUExrams532vjBwKBwK3AUwnepuiuHCB2qQ7k+UkxDQgEAjcCl+pZk2/eng/j331dTAMCgcBVwWqx8r09X7q0mXVxU9J3jWRAIBC4ARimuLec6+Nbw2Jl1x4vlu9mo0AgELgJeGsXUrPP6FRvsVw6MYBAIHBHsJ3XUr0L6VKEsHYZ1j2BQCBwL/D69Okci/+5it+qcO6Q7jeSAYFA4Ppg/eyPcnxrKKZdnVkRHoMLBAKBO4LNgyNv9pVNs2V9hMVX6S0QCARuC4YTLUI4l2N0992zkIBAIHAPsBxGHfpgl02UIdj7cTgHBAKBq4ExGw27kI5VnW0RTt+Gc0AgELgFeLUWcC6Nr+HEsC6uFKTfLS4AgUDgGuAfXUAgEAgEAoFAIBAIBAKBQCAQCAQ+MvgfowFRJtozjAcAAAAASUVORK5CYII\u003d",
             name="NewOTPDevice">
   </rax-auth:otpDevice>
   
   

**Example:  Add a moble phone HTTP response header: JSON**


.. code::

   HTTP/1.1 200 OK
   Content-Length: 1985
   Content-Type: application/json
   LOCATION: http://identity.api.rackspacecloud.com/cloud/v2.0/users/e0fb2b4ddb594819b697d0048614c117/RAX-AUTH/multi-factor/otp-devices/a34b5e4a1ffe4514a8859716136dc7cb
   Date: Tue, 05 May 2015 14:09:02 GMT





**Example:  Add a moble phone response: JSON**


.. code::

   {
       "RAX-AUTH:otpDevice": {
           "id": "58c4e0f6ca9745a9b97bcad9796685cd",
           "keyUri": "otpauth://totp/Rackspace:AngelaTestMobile1?secret=IU4K3ZYVOKKCI4Z3UZTSKBXOCWMXVGLW&issuer=Rackspace",
           "name": "NewOTPDevice",
           "qrcode": "data:image/png;base64,tVBORw0KGgoAAAANSUhEUgAAAoAAAAKAAQAAAAAktvSOAAADQUlEQVR42u3dS3KrMBCF4WbEMlgqLJVlMELXwRI6rQeRkztK/UxSEPw5I5X6oY6F/3wZICAgICAgICAgICAgICAgICDgHwcPy9f0ulvej3dbz9eT191p89fd++F1LWGTDy2AgICAY2B6ErYInteLa8h3+VvuN6uPAwICAn4LbnFRmq7FLErpLi5fZ1q35vTVfr0DBAQE/BS0Ke2g5rQ9it8SHwICAgL+GrzCrynHazE0CykY80sbICAg4GeghmbXazEKKxesRX4Mx3qAgICAnbTzNvDjozw2ICAgYPNqJHtMEkGZGK3RAwICAsblK+2LJlfruotcc65upevMSaIFEBAQcASU1M/6zvloA08OzUxrXekPkQ8AAgICPoNHEZPlRND9drlZ0lguAAICAo6BdZ+g+Ttz+6IzhW2+axAQEBDwe1D3RZa3QDEflAlpHsw7qHZoBggICNisSfnUjy5mvke56uOxZqwHCAgI2EkE6e/3dj1rK/NB8zuBFAABAQHHQC2bxyS05fDr/uxaltsDICAg4EdgrJD7LPLN6wqnVTFLy9fRbhcEBAQEbB6F0NJ4uW65tFB1/qq1HgICAgI+gbucuGrukqTktdYrHCAgIOAgGMqSuiSJzM3l2osgDhAQEHAI9NNw9IDD4Vp25Fv8gVBAQEDAATDICK6zcb6zMazrPgphvZI6ICAgYLuBR4YB5lr6WT201Fi4nvXZckBAQMARUNM7MtP4zg6Zn13hjoACAgICDoDlvkibk+ecK9KHz0chAAEBAbfe/5NqvJ2TPdYiHpcvQEBAwM5mKfiuZJcWCqEasl4N6wIEBAQcBKWkvhRdg7llx6eMQlH5AgQEBHwGtYLVeE2yz6FYzJ4SQYCAgIDdzVLotOz4oxAy7KLTnAwICAjYOblQThLV6nk1PsfMiiGlgICAgIOgBmNHMV60cX68McgLEBAQcAz07YL+Q6Gc+ydJaEBAQMCfgnXzoMmEQG31eZj3BQgICDgA7i1CQ7O5PE0OCAgIOAr60MxP4jJzU7p0wWqPVQcEBATcHkrq5o5CBNfOc7iWHflvndY9WwEICAi4PJbUf3EBAgICAgICAgICAgICAgICAgL+VfAf+kH5tccf0ykAAAAASUVORK5CYII=",
           "verified": false
       }
   }




