.. _get-identity-provider-v2.0:

Get IDP
~~~~~~~

.. code::

   GET /v2.0/RAX-AUTH/federation/identity-providers/{identityProviderId}

Get an Identity provider.

This table shows the possible response codes for this operation:

.. note::

   - User-admin or User-manage can retrieve an Identity Provider only if
     their domain is the same as the specified Identity Provider’s (IDP’s)
     ``approvedDomainId``.
   - A user with the role rcn:admin can retrieve an Identity Provider if
     their domain is within the same RCN as the IDP’s specified
     ``approvedDomainId``.

.. csv-table::
   :header: Response Code, Name, Description
   :widths: 15 25 60

   200, OK, The request has succeeded.
   403, Forbidden, Caller does not have appropriate role.
   404, Not Found, The requested resource was not found.

Request
-------

This table shows the header parameters for the request:

.. csv-table::
   :header: Name, Type, Description
   :widths: 2, 2, 2

   X-Auth-Token, String *(Required)*, A valid authentication token.

Response
--------

**Example:  Get IDP: XML response**

.. code::

   < HTTP/1.1 200 OK
   < vary:  Accept, Accept-Encoding, X-Auth-Token
   < Content-Type: application/xml

    <?xml version="1.0" encoding="UTF-8"?>
    <identityProvider id="asdfqwerr" name="name" issuer="https://my.issuer.com" authenticationUrl="https://my.login.com" description="A description" federationType="DOMAIN"
                      xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
            xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
            xmlns:atom="http://www.w3.org/2005/Atom" xmlns:identity="http://docs.openstack.org/identity/api/v2.0">
        <publicCertificates>
            <publicCertificate id="7d2bf0ecd98d2cb0f5c42ef6ae0edf4da985459b" pemEncoded="MIICsDCCAhmgAwIBAgIJAPdQ9ZKjtRX5MA0GCSqGSIb3DQEBBQUAMEUxCzAJBgNVBAYTAkFVMRMwEQYDVQQIEwpTb21lLVN0YXRlMSEwHwYDVQQKExhJbnRlcm5ldCBXaWRnaXRzIFB0eSBMdGQwHhcNMTQwODA2MTkxMzE4WhcNMjQwODA1MTkxMzE4WjBFMQswCQYDVQQGEwJBVTETMBEGA1UECBMKU29tZS1TdGF0ZTEhMB8GA1UEChMYSW50ZXJuZXQgV2lkZ2l0cyBQdHkgTHRkMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDiqa9KxLhEbMWXZsI1v/4OA0X8sAl3sglfsPMHnGjyIwB2Kz4Pl38in0/8p3ngLHyI2/XOMQwAVZxOZ7sMwHq8FY4YgdkwqxFZ1esnASS6ty1286MJYWo+uDwUepH4A4cKtqUKgIsT4VOxyXSDzreZPvWjFDNDsq+w42UnpI0s6QIDAQABo4GnMIGkMB0GA1UdDgQWBBQ4+BePfVmEY4wY/gLAgec3J3J7JDB1BgNVHSMEbjBsgBQ4+BePfVmEY4wY/gLAgec3J3J7JKFJpEcwRTELMAkGA1UEBhMCQVUxEzARBgNVBAgTClNvbWUtU3RhdGUxITAfBgNVBAoTGEludGVybmV0IFdpZGdpdHMgUHR5IEx0ZIIJAPdQ9ZKjtRX5MAwGA1UdEwQFMAMBAf8wDQYJKoZIhvcNAQEFBQADgYEAxD4+TDo+/MzQKg3fH0HazXsSKQN1V9crvVe36VUQ79tIkufXATcwBlbA+SkkCpt68c0mfwKgffy2KucNhLMhBUzzF+M8k9X07IgfmrAviOd3D5PqEoNpkP/am8RMm7mjSC/DPb1Jd+yRFB8I0vUmFp8G+ZJ+F00zqabtCv/kMVM=" />
            <publicCertificate id="7d2bf0ecd98d2cb0f5c42ef6ae0edf4da985459b" pemEncoded="MIICsDCCAhmgAwIBAgIJAPdQ9ZKjtRX5MA0GCSqGSIb3DQEBBQUAMEUxCzAJBgNVBAYTAkFVMRMwEQYDVQQIEwpTb21lLVN0YXRlMSEwHwYDVQQKExhJbnRlcm5ldCBXaWRnaXRzIFB0eSBMdGQwHhcNMTQwODA2MTkxMzE4WhcNMjQwODA1MTkxMzE4WjBFMQswCQYDVQQGEwJBVTETMBEGA1UECBMKU29tZS1TdGF0ZTEhMB8GA1UEChMYSW50ZXJuZXQgV2lkZ2l0cyBQdHkgTHRkMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDiqa9KxLhEbMWXZsI1v/4OA0X8sAl3sglfsPMHnGjyIwB2Kz4Pl38in0/8p3ngLHyI2/XOMQwAVZxOZ7sMwHq8FY4YgdkwqxFZ1esnASS6ty1286MJYWo+uDwUepH4A4cKtqUKgIsT4VOxyXSDzreZPvWjFDNDsq+w42UnpI0s6QIDAQABo4GnMIGkMB0GA1UdDgQWBBQ4+BePfVmEY4wY/gLAgec3J3J7JDB1BgNVHSMEbjBsgBQ4+BePfVmEY4wY/gLAgec3J3J7JKFJpEcwRTELMAkGA1UEBhMCQVUxEzARBgNVBAgTClNvbWUtU3RhdGUxITAfBgNVBAoTGEludGVybmV0IFdpZGdpdHMgUHR5IEx0ZIIJAPdQ9ZKjtRX5MAwGA1UdEwQFMAMBAf8wDQYJKoZIhvcNAQEFBQADgYEAxD4+TDo+/MzQKg3fH0HazXsSKQN1V9crvVe36VUQ79tIkufXATcwBlbA+SkkCpt68c0mfwKgffy2KucNhLMhBUzzF+M8k9X07IgfmrAviOd3D5PqEoNpkP/am8RMm7mjSC/DPb1Jd+yRFB8I0vUmFp8G+ZJ+F00zqabtCv/kMVM=" />
        </publicCertificates>
        <approvedDomainIds>
            <approvedDomainId>12345</approvedDomainId>
        </approvedDomainIds>
    </identityProvider>

**Example:  Get IDP: JSON response**

.. code::

   < HTTP/1.1 200 OK
   < vary:  Accept, Accept-Encoding, X-Auth-Token
   < Content-Type: application/json

    {
      "RAX-AUTH:identityProvider": {
        "id": "adsdfwejjbwerh",
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
          {
            "id":"7d2bf0ecd98d2cb0f5c42ef6ae0edf4da985459b",
            "pemEncoded":"MIICsDCCAhmgAwIBAgIJAPdQ9ZKjtRX5MA0GCSqGSIb3DQEBBQUAMEUxCzAJBgNVBAYTAkFVMRMwEQYDVQQIEwpTb21lLVN0YXRlMSEwHwYDVQQKExhJbnRlcm5ldCBXaWRnaXRzIFB0eSBMdGQwHhcNMTQwODA2MTkxMzE4WhcNMjQwODA1MTkxMzE4WjBFMQswCQYDVQQGEwJBVTETMBEGA1UECBMKU29tZS1TdGF0ZTEhMB8GA1UEChMYSW50ZXJuZXQgV2lkZ2l0cyBQdHkgTHRkMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDiqa9KxLhEbMWXZsI1v/4OA0X8sAl3sglfsPMHnGjyIwB2Kz4Pl38in0/8p3ngLHyI2/XOMQwAVZxOZ7sMwHq8FY4YgdkwqxFZ1esnASS6ty1286MJYWo+uDwUepH4A4cKtqUKgIsT4VOxyXSDzreZPvWjFDNDsq+w42UnpI0s6QIDAQABo4GnMIGkMB0GA1UdDgQWBBQ4+BePfVmEY4wY/gLAgec3J3J7JDB1BgNVHSMEbjBsgBQ4+BePfVmEY4wY/gLAgec3J3J7JKFJpEcwRTELMAkGA1UEBhMCQVUxEzARBgNVBAgTClNvbWUtU3RhdGUxITAfBgNVBAoTGEludGVybmV0IFdpZGdpdHMgUHR5IEx0ZIIJAPdQ9ZKjtRX5MAwGA1UdEwQFMAMBAf8wDQYJKoZIhvcNAQEFBQADgYEAxD4+TDo+/MzQKg3fH0HazXsSKQN1V9crvVe36VUQ79tIkufXATcwBlbA+SkkCpt68c0mfwKgffy2KucNhLMhBUzzF+M8k9X07IgfmrAviOd3D5PqEoNpkP/am8RMm7mjSC/DPb1Jd+yRFB8I0vUmFp8G+ZJ+F00zqabtCv/kMVM="
          }
        ]
      }
    }
