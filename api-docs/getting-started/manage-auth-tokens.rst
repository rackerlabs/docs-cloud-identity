.. _manage-auth-tokens:

============================
Manage authentication tokens
============================

Authentication tokens are valid for 24 hours by default. The expiration
time stamp is included in the token object returned in the
authentication response. Administrators and users can invalidate a token
immediately by submitting a **Revoke token** API request to the Identity
service endpoint.

If you re-authenticate before the `token` expires, the Identity
service returns a new token.

When a token expires or becomes invalid, any API request submitted
against Rackspace Cloud services returns a 401 error message. To regain
access, submit another **POST tokens** request to the authentication
endpoint.

.. _best-practices-token-management:

Best practices
~~~~~~~~~~~~~~

-  When you authenticate to the Rackspace Identity service be sure to
   cache the token value that is returned.

   The Rackspace Identity service validates the authentication in every
   API request before attempting to complete the operation. To optimize your
   API operations and reduce system load, store the
   authentication token in a secure cache or database so that applications
   can use the stored value instead of requiring the application to issue
   an authentication request before each API operation. You can re-use the cached
   token value as long as it remains valid.

   .. note::

      For an example of how to cache credentials with an SDK, see
      `Caching credentials`_ in the php-opencloud documentation.

-  Design applications to re-authenticate after receiving a
   `401 Unauthorized` response from a service endpoint, or use
   either of the following methods to check the token expiration and
   reauthenticate before the token expires.

   -  Submit a **POST tokens** request within an hour of the token
      expiration to obtain a new token. Note that this behavior is a
      Rackspace customization of the OpenStack Identity (keystone)
      implementation.

   -  Submit a **DELETE token** request to revoke the existing
      token, and then submit another **POST tokens** request to get a new
      token.

-  To simplify authentication, credential, and token management, use an
   `OpenStack command-line client application`_ or one of the
   `Rackspace SDKs`_.

Learn more
~~~~~~~~~~

Visit the following links to learn more about the Identity service.

-  :ref:`Token operations API reference <token-operations>`

-  :ref:`Identity concepts <concepts>`

-  :ref:`Annotated request and response <annotated-auth-req-resp>`

-  :ref:`Identity API operations reference <api-reference>`

-  `API operations references for other Rackspace services`_

..  tip::
    You can find language binding examples that can be modified to work with
    the Rackspace Identity service in the `Rackspace Software Development
    Kits`_.


.. _Caching credentials: http://php-opencloud.readthedocs.io/en/latest/caching-creds.html
.. _API operations references for other Rackspace services: https://developer.rackspace.com/docs
.. _OpenStack command-line client application: https://wiki.openstack.org/wiki/OpenStackClients
.. _Rackspace SDKs: https://developer.rackspace.com/docs/#sdks
.. _Rackspace Software Development Kits: https://developer.rackspace.com/docs/#sdks
