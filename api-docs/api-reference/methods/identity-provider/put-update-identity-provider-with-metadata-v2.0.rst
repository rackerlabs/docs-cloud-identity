.. _put-update-identity-provider-with-metadata-v2.0:

Update IDP with metadata
~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

   PUT /v2.0/RAX-AUTH/federation/identity-providers/{identityProviderId}/metadata

Update an existing Identity Provider using XML metadata.

.. note::

   - Only IDP's authentication url and certificates are allowed to be updated
     via metadata.

This table shows the possible response codes for this operation:

.. csv-table::
   :header: Response Code, Name, Description
   :widths: auto

   200, OK, The request has been fulfilled.
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

This table shows the header parameters for the request:

.. csv-table::
   :header: Name, Type, Description
   :widths: auto

   X-Auth-Token, String *(Required)*, A valid authentication token.

This table shows the URI parameters for the request:

.. csv-table::
   :header: Name, Type, Description
   :widths: auto

   {identityProviderId}, String *(Required)*, The Identity Provider's ID.

This table shows the body parameters for the request:

.. csv-table::
   :header: Name, Type, Description
   :widths: auto

    **EntityDescriptor**, Object *(Required)*, Describes a system entity such as an Identity Provider.
    EntityDescriptor.\ **entityID**, String *(Required)*, The issuer for IDP.
    EntityDescriptor.\ **IDPSSODescriptor**, Object *(Required)*, An IDP role.
    EntityDescriptor.IDPSSODescriptor.\ **protocolSupportEnumeration**, String *(Required)*, Represents general classes of protocol support for the role in question.
    EntityDescriptor.IDPSSODescriptor.\ **SingleSignOnService**, Object *(Required)*, Describes a protocol binding endpoint.
    EntityDescriptor.IDPSSODescriptor.SingleSignOnService.\ **Binding**, String *(Optional)*, Describes a protocol binding. Only `HTTP-Redirect` is currently supported.
    EntityDescriptor.IDPSSODescriptor.SingleSignOnService.\ **Location**, String *(Optional)*, Describes the authentication url.
    EntityDescriptor.IDPSSODescriptor.\ **KeyDescriptor**, Object *(Optional)*, Associates one or more public keys with the system being defined.
    EntityDescriptor.IDPSSODescriptor.KeyDescriptor.\ **KeyInfo**, Object *(Optional)*, An element describing keys.

**Example: Update IDP request: XML**

.. code::

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

Response
--------

This table shows the header parameters for the response:

.. csv-table::
    :header: Name, Type, Description
    :widths: auto

    Location, String *(Required)*, The location URI of the newly created IDP.

**Example: Update IDP: XML response**

.. code::

    < HTTP/1.1 200 OK
    < vary:  Accept, Accept-Encoding, X-Auth-Token
    < Content-Type: application/xml

    <?xml version="1.0" encoding="UTF-8"?>
    <identityProvider id="123456" name="name" issuer="https://my.issuer.com" authenticationUrl="https://my.login.com" description="A description" federationType="DOMAIN"
                      xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
            xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
            xmlns:atom="http://www.w3.org/2005/Atom" xmlns:identity="http://docs.openstack.org/identity/api/v2.0">
        <publicCertificates>
            <publicCertificate id="7d2bf0ecd98d2cb0f5c42ef6ae0edf4da985459b" pemEncoded="MIICsDCCAhmgAwIBAgIJAPdQ9ZKjtRX5MA0GCSqGSIb3DQEBBQUAMEUxCzAJBgNVBAYTAkFVMRMwEQYDVQQIEwpTb21lLVN0YXRlMSEwHwYDVQQKExhJbnRlcm5ldCBXaWRnaXRzIFB0eSBMdGQwHhcNMTQwODA2MTkxMzE4WhcNMjQwODA1MTkxMzE4WjBFMQswCQYDVQQGEwJBVTETMBEGA1UECBMKU29tZS1TdGF0ZTEhMB8GA1UEChMYSW50ZXJuZXQgV2lkZ2l0cyBQdHkgTHRkMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDiqa9KxLhEbMWXZsI1v/4OA0X8sAl3sglfsPMHnGjyIwB2Kz4Pl38in0/8p3ngLHyI2/XOMQwAVZxOZ7sMwHq8FY4YgdkwqxFZ1esnASS6ty1286MJYWo+uDwUepH4A4cKtqUKgIsT4VOxyXSDzreZPvWjFDNDsq+w42UnpI0s6QIDAQABo4GnMIGkMB0GA1UdDgQWBBQ4+BePfVmEY4wY/gLAgec3J3J7JDB1BgNVHSMEbjBsgBQ4+BePfVmEY4wY/gLAgec3J3J7JKFJpEcwRTELMAkGA1UEBhMCQVUxEzARBgNVBAgTClNvbWUtU3RhdGUxITAfBgNVBAoTGEludGVybmV0IFdpZGdpdHMgUHR5IEx0ZIIJAPdQ9ZKjtRX5MAwGA1UdEwQFMAMBAf8wDQYJKoZIhvcNAQEFBQADgYEAxD4+TDo+/MzQKg3fH0HazXsSKQN1V9crvVe36VUQ79tIkufXATcwBlbA+SkkCpt68c0mfwKgffy2KucNhLMhBUzzF+M8k9X07IgfmrAviOd3D5PqEoNpkP/am8RMm7mjSC/DPb1Jd+yRFB8I0vUmFp8G+ZJ+F00zqabtCv/kMVM=" />
        </publicCertificates>
        <approvedDomainIds>
            <approvedDomainId>12345</approvedDomainId>
        </approvedDomainIds>
    </identityProvider>

**Example: Update IDP: JSON response**

.. code::

   < HTTP/1.1 200 OK
   < vary:  Accept, Accept-Encoding, X-Auth-Toke
   < Content-Type: application/json

    {
      "RAX-AUTH:identityProvider": {
        "id": "123456",
        "name": "name",
        "issuer": "https://my.issuer.com",
        "description": "A description",
        "federationType": "DOMAIN",
        "authenticationUrl": "https://my.login.com",
        "approvedDomainIds": [
          "12345"
        ],
        "publicCertificates": [
          {
            "id":"7d2bf0ecd98d2cb0f5c42ef6ae0edf4da985459b",
            "pemEncoded":"MIICsDCCAhmgAwIBAgIJAPdQ9ZKjtRX5MA0GCSqGSIb3DQEBBQUAMEUxCzAJBgNVBAYTAkFVMRMwEQYDVQQIEwpTb21lLVN0YXRlMSEwHwYDVQQKExhJbnRlcm5ldCBXaWRnaXRzIFB0eSBMdGQwHhcNMTQwODA2MTkxMzE4WhcNMjQwODA1MTkxMzE4WjBFMQswCQYDVQQGEwJBVTETMBEGA1UECBMKU29tZS1TdGF0ZTEhMB8GA1UEChMYSW50ZXJuZXQgV2lkZ2l0cyBQdHkgTHRkMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDiqa9KxLhEbMWXZsI1v/4OA0X8sAl3sglfsPMHnGjyIwB2Kz4Pl38in0/8p3ngLHyI2/XOMQwAVZxOZ7sMwHq8FY4YgdkwqxFZ1esnASS6ty1286MJYWo+uDwUepH4A4cKtqUKgIsT4VOxyXSDzreZPvWjFDNDsq+w42UnpI0s6QIDAQABo4GnMIGkMB0GA1UdDgQWBBQ4+BePfVmEY4wY/gLAgec3J3J7JDB1BgNVHSMEbjBsgBQ4+BePfVmEY4wY/gLAgec3J3J7JKFJpEcwRTELMAkGA1UEBhMCQVUxEzARBgNVBAgTClNvbWUtU3RhdGUxITAfBgNVBAoTGEludGVybmV0IFdpZGdpdHMgUHR5IEx0ZIIJAPdQ9ZKjtRX5MAwGA1UdEwQFMAMBAf8wDQYJKoZIhvcNAQEFBQADgYEAxD4+TDo+/MzQKg3fH0HazXsSKQN1V9crvVe36VUQ79tIkufXATcwBlbA+SkkCpt68c0mfwKgffy2KucNhLMhBUzzF+M8k9X07IgfmrAviOd3D5PqEoNpkP/am8RMm7mjSC/DPb1Jd+yRFB8I0vUmFp8G+ZJ+F00zqabtCv/kMVM="
          },
        ]
      }
    }
