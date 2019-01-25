.. _auth-config-mfa-phone:

Set up multi-factor authentication by mobile phone
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Use these instructions to add a mobile phone to a Rackspace Cloud
account and configure it for multi-factor authentication by using the
Identity service API. You can also complete this process through the
Cloud Control panel.

..  note::

    -  Multi-factor authentication applies only to username and password
       credentials. You cannot use it to secure username and API key
       credentials.

    -  Users with a multi-factor authenticated account can only use
       OpenStack or Rackspace CLI tools that support username and API key
       authentication or token authentication, like the Nova client.

       For token authentication, submit an authentication request. Then,
       export the returned token to the CLI environment variable,
       `OS_TOKEN` or `OS_AUTH_TOKEN` for example. After you set the
       token, you can submit API requests by using the CLI.

    -  When multi-factor is enabled on an account, any existing tokens for
       that user are immediately revoked.

    -  Multi-factor authentication requires the Identity
       service, version 2.0 or later. User accounts that have been
       configured for multi-factor authentication cannot authenticate using
       Identity API version 1.1 or earlier.

    -  If the authentication response returns a `403 Forbidden` error
       message with a request to setup multi-factor authentication, your
       account has been restricted. To regain access, :ref:`submit a request for
       a multi-factor scoped authentication token <req-mfa-setup-token>`
       that you can use to set up your account.



#.  Authenticate to the Identity service to obtain an authentication token.

   **Request**

       .. code::

          $ curl https://identity.api.rackspacecloud.com/v2.0/tokens \
                 -X POST \
                 -H "Accept: application/json" \
                 -d '{"auth": {"passwordCredentials": {"username":"jqsmith", "password":"Password1"}}}' \
                 -H "Content-Type: application/json"


   **Response**

   The Identity service returns a 200 response code that includes
   the authentication token ID.

   .. code::

      < HTTP/1.1 200 OK
      < Vary:  Accept, Accept-Encoding, X-Auth-Token
      < Content-Type: application/json
      < Content-Length: 375
      < Server: Jetty(6.1.25)
      <
      {
         "access": {
             "serviceCatalog": [],
               "token": {
                 "RAX-AUTH:authenticatedBy": [
                      "PASSWORD"
                  ],
                 "expires": "2013-12-17T22:47:04.253-06:00",
                 "id": "xxxxxxxxxxxxxxxxxxx"
              },
             "user": {
                  "RAX-AUTH:defaultRegion": "IAD",
                  "RAX-AUTH:federated": false,
                  "id": "a64ee2047fc14cc7bc977caa3cfff35f",
                  "name": "jqsmith",
                  "roles": [
                      {
                         "description": "User Admin Role.",
                         "id": "3",
                         "name": "identity:user-admin"
                      }
                  ]
             }
         }
     }


#. Add a mobile phone to your account.

   **Request**

  .. code::

     $ curl $AUTH_URL/v2.0/users/$USER_ID/RAX-AUTH/multi-factor/mobile-phones  \
             -X POST \
             -H "Content-Type: application/json" \
             -H "X-Auth-Token: $AUTH_TOKEN"
             -d '{"RAX-AUTH:mobilePhone": { "number": "+1 512-555-1000" }}' \
             | python -m json.tool


   ..  tip::

       Specify the phone number in `E.123
       notation <https://www.itu.int/rec/T-REC-E.123-200102-I/en>`__, for example,
       ``+1 235 435 6234`` or ``+44 42 1123 4567``.


   **Response**

   The Identity service returns a 201 response that includes the
   system-generated phone ID.

   .. code::

      < HTTP/1.1 201 Created
      < Vary:  Accept, Accept-Encoding, X-Auth-Token
      < Location: http://localhost:8083/idm/cloud/v2.0/users/a64ee2047fc14cc7bc977caa3cfff35f/RAX-AUTH/multi-factor/mobile-phones/889a7245f49e4ab789ebaebf91c0f1eb
      < Content-Type: application/json
      < Content-Length: 93
      < Server: Jetty(6.1.25)
      <
      {
          "RAX-AUTH:mobilePhone": {
             "id": "1234321245f49e4ab789ebaebf91c0f1eb",
             "number": "+1 512-555-0100"
          }
      }


   ..  tip::

       Export the phone `id` value to an environment variable, so you can
       use it to complete the phone verification process.

   .. code::

      $ EXPORT PHONE_ID=""1234321245f49e4ab789ebaebf91c0f1eb"


#. Send a verification code to your phone to confirm that you possess
   the phone associated with your account.

   Include the phone `id` value (or the $PHONE\_ID environment
   variable that you exported) from the add mobile phone operation
   response in the API request.

   **Request**

   .. code::

      $ curl $AUTH_URL/v2.0/users/$USER_ID/RAX-AUTH/multi-factor/mobile-phones/$PHONE_ID/verificationcode \
             -X POST \
             -H "Content-Type: application/json" \
             -H "Accept: application/json" \
             -H "X-Auth-Token: $AUTH_TOKEN"
             | python -m json.tool

   **Response**

   Identity service returns a 201 response and sends a message like
   this to the designated phone number:

   `To verify this mobile device for your Rackspace profile used for multi-factor authentication enter the PIN 1732`.

#. Return the verification PIN code to complete the phone verification process.

   **Request**

   .. code::

      $ curl $AUTH_URL/v2.0/users/$USER_ID/RAX-AUTH/multi-factor/mobile-phones/$PHONE_ID/verify \
             -X POST \
             -H "Content-Type: application/json" \
             -H "Accept: application/json" \
             -d '{"RAX-AUTH:verificationCode": { "code": "1732" }}' \
             -H "X-Auth-Token: $AUTH_TOKEN" \
             | python -m json.tool

   **Response**

   The Identity service returns a 202 response.

   .. code::

      < HTTP/1.1 202 Accepted
      < Vary:  Accept, Accept-Encoding, X-Auth-Token
      < Content-Type: application/json
      < Server: Jetty(6.1.25)


#. Update your account to enable multi-factor authentication support.

   **Request**

   .. code::

      $ curl $AUTH_URL/v2.0/users/$USER_ID/RAX-AUTH/multi-factor \
             -X PUT \
             -H "Content-Type: application/json" \
             -H "Accept: application/json" \
             -d '{"RAX-AUTH:multiFactor": {"enabled": true }}' \
             -H "X-Auth-Token: $AUTH_TOKEN" \
             | python -m json.tool


   **Response**

   The Identity service returns a 204 response.

   .. code::

      < HTTP/1.1 204 No Content
      < Vary:  Accept, Accept-Encoding, X-Auth-Token
      < Content-Type: application/json
      < Server: Jetty(6.1.25)

After you set up and enable multi-factor authentication, follow the
steps to :ref:`auth-mfa-enabled-account`.
