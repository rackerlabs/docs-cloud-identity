.. _get-identity-provider-metadata-v2.0:

Get metadata for IDP
~~~~~~~~~~~~~~~~~~~~

.. code::

   GET /v2.0/RAX-AUTH/federation/identity-providers/{identityProviderId}/metadata

Retrieve an Identity Provider's XML metadata.

This table shows the possible response codes for this operation:

.. csv-table::
   :header: Response Code, Name, Description
   :widths: auto

   200, OK, The request has been fulfilled.
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

Response
--------

**Example:  Get IDP's metadata: XML response**

.. code::

    < HTTP/1.1 200 OK
    < vary:  Accept, Accept-Encoding, X-Auth-Token
    < Content-Type: application/xml

    <?xml version="1.0" encoding="UTF-8"?>
    <ns0:EntityDescriptor xmlns:ns0="urn:oasis:names:tc:SAML:2.0:metadata"
        xmlns:ns1="http://www.w3.org/2000/09/xmldsig#"
        xmlns:ns2="urn:oasis:names:tc:SAML:metadata:algsupport"
        ID="someId" entityID="https://my.issuer.com">
        <ns0:IDPSSODescriptor protocolSupportEnumeration="urn:oasis:names:tc:SAML:2.0:protocol">
            <ns0:KeyDescriptor use="signing">
                <ns1:KeyInfo>
                    <ns1:X509Data>
                        <ns1:X509Certificate>
                        MIICsDCCAhmgAwIBAgIJAPdQ9ZKjtRX5MA0GCSqGSIb3DQEBBQUAMEUxCzAJBgNV
                        BAYTAkFVMRMwEQYDVQQIEwpTb21lLVN0YXRlMSEwHwYDVQQKExhJbnRlcm5ldCBX
                        aWRnaXRzIFB0eSBMdGQwHhcNMTQwODA2MTkxMzE4WhcNMjQwODA1MTkxMzE4WjBF
                        MQswCQYDVQQGEwJBVTETMBEGA1UECBMKU29tZS1TdGF0ZTEhMB8GA1UEChMYSW50
                        ZXJuZXQgV2lkZ2l0cyBQdHkgTHRkMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKB
                        gQDiqa9KxLhEbMWXZsI1v/4OA0X8sAl3sglfsPMHnGjyIwB2Kz4Pl38in0/8p3ng
                        LHyI2/XOMQwAVZxOZ7sMwHq8FY4YgdkwqxFZ1esnASS6ty1286MJYWo+uDwUepH4
                        A4cKtqUKgIsT4VOxyXSDzreZPvWjFDNDsq+w42UnpI0s6QIDAQABo4GnMIGkMB0G
                        A1UdDgQWBBQ4+BePfVmEY4wY/gLAgec3J3J7JDB1BgNVHSMEbjBsgBQ4+BePfVmE
                        Y4wY/gLAgec3J3J7JKFJpEcwRTELMAkGA1UEBhMCQVUxEzARBgNVBAgTClNvbWUt
                        U3RhdGUxITAfBgNVBAoTGEludGVybmV0IFdpZGdpdHMgUHR5IEx0ZIIJAPdQ9ZKj
                        tRX5MAwGA1UdEwQFMAMBAf8wDQYJKoZIhvcNAQEFBQADgYEAxD4+TDo+/MzQKg3f
                        H0HazXsSKQN1V9crvVe36VUQ79tIkufXATcwBlbA+SkkCpt68c0mfwKgffy2KucN
                        hLMhBUzzF+M8k9X07IgfmrAviOd3D5PqEoNpkP/am8RMm7mjSC/DPb1Jd+yRFB8I
                        0vUmFp8G+ZJ+F00zqabtCv/kMVM=
                        </ns1:X509Certificate>
                    </ns1:X509Data>
                </ns1:KeyInfo>
            </ns0:KeyDescriptor>
            <ns0:SingleSignOnService Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-Redirect" Location="https://my.login.com"/>
        </ns0:IDPSSODescriptor>
    </ns0:EntityDescriptor>
