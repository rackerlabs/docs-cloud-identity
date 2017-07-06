.. _put-add-cert-to-identity-provider-v2.0:

Add public certificate to IDP
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

   POST /v2.0/RAX-AUTH/federation/identity-providers/{identityProviderId}/certificates

Add a new public certificate to an Identity Provider.

This table shows the possible response codes for this operation:

.. csv-table::
   :header: Response Code, Name, Description
   :widths: auto

   204, No Content, The request has been fulfilled. The public certificate
   has been added to the IDP.
   400, Bad Request, "The request is missing one or more elements, or
   the values of some elements are invalid."
   401, Unauthorized, "You are not authorized to complete this operation.
   This error can occur if the request is submitted with an invalid
   authentication token."
   403, Forbidden, "The request was valid, but the server is refusing to
   respond because you do not have permission to access the requested
   resource. Submit a request to your account administrator to
   determine how to gain access."
   404, Not Found, The requested resource was not found.
   405, Invalid Method, "The method specified in the request is not valid for
   the resource identified in the request URI."
   406, Not Acceptable, The server cannot send data in a format requested.
   413, Over Limit, The number of items returned is above the allowed limit.
   503, Service Fault, Service is not available.

Request
-------

This table shows the URI parameters for the request:

.. csv-table::
    :header: Name, Type, Description
    :widths: auto

    identityProviderId, String *(Required)*, The ID of the identity provider.

This table shows the header parameters for the request:

.. csv-table::
   :header: Name, Type, Description
   :widths: auto

   X-Auth-Token, String *(Required)*, A valid authentication token.

This table shows the body parameters for the request:

.. csv-table::
   :header: Name, Type, Description
   :widths: auto

    **publicCertificate**, Object *(Required)*, The public certificate to add to the IDP.
    publicCertificate.\ **pemEncoded**, String *(Required)*, The pem encoded string for the public certificate.

**Example: Add public certificate to IDP request: XML**

.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <publicCertificate  xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
                        xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
                        xmlns:atom="http://www.w3.org/2005/Atom" xmlns:identity="http://docs.openstack.org/identity/api/v2.0"
        pemEncoded="MIICsDCCAhmgAwIBAgIJAPdQ9ZKjtRX5MA0GCSqGSIb3DQEBBQUAMEUxCzAJBgNVBAYTAkFVMRMwEQYDVQQIEwpTb21lLVN0YXRlMSEwHwYDVQQKExhJbnRlcm5ldCBXaWRnaXRzIFB0eSBMdGQwHhcNMTQwODA2MTkxMzE4WhcNMjQwODA1MTkxMzE4WjBFMQswCQYDVQQGEwJBVTETMBEGA1UECBMKU29tZS1TdGF0ZTEhMB8GA1UEChMYSW50ZXJuZXQgV2lkZ2l0cyBQdHkgTHRkMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDiqa9KxLhEbMWXZsI1v/4OA0X8sAl3sglfsPMHnGjyIwB2Kz4Pl38in0/8p3ngLHyI2/XOMQwAVZxOZ7sMwHq8FY4YgdkwqxFZ1esnASS6ty1286MJYWo+uDwUepH4A4cKtqUKgIsT4VOxyXSDzreZPvWjFDNDsq+w42UnpI0s6QIDAQABo4GnMIGkMB0GA1UdDgQWBBQ4+BePfVmEY4wY/gLAgec3J3J7JDB1BgNVHSMEbjBsgBQ4+BePfVmEY4wY/gLAgec3J3J7JKFJpEcwRTELMAkGA1UEBhMCQVUxEzARBgNVBAgTClNvbWUtU3RhdGUxITAfBgNVBAoTGEludGVybmV0IFdpZGdpdHMgUHR5IEx0ZIIJAPdQ9ZKjtRX5MAwGA1UdEwQFMAMBAf8wDQYJKoZIhvcNAQEFBQADgYEAxD4+TDo+/MzQKg3fH0HazXsSKQN1V9crvVe36VUQ79tIkufXATcwBlbA+SkkCpt68c0mfwKgffy2KucNhLMhBUzzF+M8k9X07IgfmrAviOd3D5PqEoNpkP/am8RMm7mjSC/DPb1Jd+yRFB8I0vUmFp8G+ZJ+F00zqabtCv/kMVM="/>

Response
--------

This operation does not return a response body.
