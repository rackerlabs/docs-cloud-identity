.. _post-add-domain-trust:

Add domain trust
~~~~~~~~~~~~~~~~

.. code::

    POST v2.0/RAX-AUTH/trusts

Create a domain trust.

.. note::

    - If the user creating the domain trust is a ``user-admin`` or
      ``user-manager``, the principal domain is set to the caller's domain.
    - Users with the role ``identity:domain-trust-admin`` can create domain
      trust for any principal and delegate domain.
    - Use the RAX-AUTH API extension to the Core Identity API to implement this
      API operation.

The following table shows the possible response codes for this operation:

.. csv-table::
  :header: Response code, Name, Description
  :widths: 2, 2, 2

    201, Created, The request has been fulfilled. The domain trust has been created.
    400, Bad Request, The request was invalid.
    401, Unauthorized, You are not authorized to complete this operation. This error can occur if the request is submitted with an invalid authentication token.
    403, Forbidden, Caller does not have an appropriate role.
    405, Invalid Method, The method specified in the request is not valid for the resource identified in the request URI.
    409, Conflict, A domain trust already exists for the given delegate and principal domains.
    503, Service Fault, Service is not available.

-------
Request
-------

The following table shows the body parameters for the request:

.. csv-table::
  :header: Name, Type, Description
  :widths: 2, 2, 2

    domainTrust, Object, A ``domainTrust`` object that specifies the domain trust information.
    domainTrust.\ **delegateDomain**, String *(Required)*, The domain that will be using the domain trust for authentication.
    domainTrust.\ **principalDomain**, String *(Required)*, The domain that users of the domain trust will be authenticating into.
    domainTrust.\ **name**, String *(Required)*, The name of the domain trust.
    domainTrust.\ **description**, String *(Optional)*, A description of the domain trust.

**Example: Add domain trust JSON Request**

.. code::

    {
        "domainTrust": {
            "delegateDomain": "07f25c743f204778977804618e39f817",
            "name": "DomainTrust123",
            "principalDomain": "5aada1b7838c4366898d64654313ac81",
            "description": "Domain trust to give users observer and ticketing permissions"
        }
    }

--------
Response
--------

The following table shows the response headers for create trust:

.. csv-table::
  :header: Name, Type, Description
  :widths: 2, 2, 2

  X-Accept-Code, Header string, A one-time secure domain trust code used for accepting a domain trust.

**Example: Add domain trust JSON Response**

.. code::

    {
        "domainTrust": {
            "id": "f97e9b424a154f38a4989732c69a9a10",
            "delegateDomain": "07f25c743f204778977804618e39f817",
            "name": "DomainTrust123",
            "principalDomain": "5aada1b7838c4366898d64654313ac81",
            "description": "Domain trust to give users observer and ticketing permissions"
        }
    }
