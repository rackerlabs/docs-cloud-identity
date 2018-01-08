.. _put-update-identity-provider-v2.0:

Update IDP
~~~~~~~~~~

.. code::

   PUT /v2.0/RAX-AUTH/federation/identity-providers/{identityProviderId}

Update an Identity provider.

.. note::

   - User-admin or User-manage can make a request only when caller's domain is the same as the specified Identity Provider's (IDP's) approvedDomainId.
   - User-admin or User-manage can update the name, description and emailDomains. Any specified values for other fields are ignored.
   - User with the role rcn:admin can make a request only when caller's domain is within the same RCN as the IDP's specified approvedDomainId.
   - User with the role rcn:admin can update the name, description and approvedDomainId. Any specified values for other fields are ignored.

This table shows the possible response codes for this operation:

.. csv-table::
   :header: Response code, Name, Description
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
   409, Conflict, The request could not be completed due to a conflict with the current state of the target resource.
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
   :widths: 2, 2, 2

    RAX-AUTH:identityProvider, Object, A ``identity-provider`` object that specifies the IDP information.
    RAX-AUTH:identityProvider.\ **name**, String *(Optional)*, "The name of the provider. Must consist of only alphanumeric, '-', '.', and be less than 255 characters."
    RAX-AUTH:identityProvider.\ **description**, String *(Optional)*, "Blurb to describe the IDP. Used for informative purposes only."
    RAX-AUTH:identityProvider.\ **approvedDomainIds**, Object *(Optional)*, Limits the IDP to only authenticating for the specified domains. Mutually exclusive w/ approvedDomainGroup.
    RAX-AUTH:identityProvider.\ **emailDomains**, Object *(Optional)*, List of email domains.
    RAX-AUTH:identityProvider.emailDomains.\ **emailDomain**, String *(Optional)*, String representing an email domain. Value must be unique across all identity providers.

**Example: Update IDP request: XML**

.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <identityProvider name="name" description="A description"
                      xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
            xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
            xmlns:atom="http://www.w3.org/2005/Atom" xmlns:identity="http://docs.openstack.org/identity/api/v2.0">
        <approvedDomainIds>
            <approvedDomainId>12345</approvedDomainId>
        </approvedDomainIds>
        <emailDomains>
            <emailDomain>emailDomain.com</emailDomain>
        </emailDomains>
    </identityProvider>

**Example: Update IDP request: JSON**

.. code::

    {
      "RAX-AUTH:identityProvider": {
        "name": "name",
        "description": "A description",
        "approvedDomainIds": [
            "12345"
        ],
        "emailDomains": [
            "emailDomain.com"
        ]
      }
    }

Response
--------

**Example:  Update IDP: XML response**

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
        <emailDomains>
            <emailDomain>emailDomain.com</emailDomain>
        </emailDomains>
    </identityProvider>

**Example:  Update IDP: JSON response**

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
        "emailDomains": [
            "emailDomain.com"
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
