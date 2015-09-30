.. _auth-add-mfa-enforcement:

Add multi-factor authentication enforcement policy to Rackspace Cloud accounts
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Rackspace Cloud account administrators can configure multi-factor authentication 
enforcement policy across a domainand, optionally, 
:ref:`customize them at the user level <auth-add-mfa-user-enforcement>`.


.. important:: 
   To configure domain-level enforcment, your Administrator account must be
   :ref:`configured for multi-factor authentication <auth-mfa-setup>`. 
   
   
.. _auth-add-mfa-domain-enforcement:

Update domain-level multi-factor authentication enforcement
...............................................................

To set domain-level enforcement, use the 
:ref:`update domain enforcement settings for multi-factor authentication operation <multifactor-operations>` 
to enforce multi-factor authentication requirements for all user accounts within a specified domain.

-  Set the enforcement level to `REQUIRED` to make multi-factor
   authentication mandatory for accounts within a specified domain.

-  Set the enforcement level to `OPTIONAL` to make multi-factor
   authentication optional for all users.

Administrators can update the domain-level enforcement setting from the
API or the Cloud Control Panel. The following figure shows the API work
flow for updating domain enforcement settings.

 
**Figure: API workflow for domain-level enforcement of multi-factor
authentication**

.. figure::  ../_images/mfa-domain-level-state-transitions.png
   :alt: API workflow for domain-level enforcement of multi-factor authentication

The following example shows the API request to update domain enforcement
settings for a domain. The example assumes the following credentials and
account information: an authenticated user administrator with a valid
admin token (`$ADMIN_TOKEN`) and the ID of the domain (`$DOMAIN_ID`)
to update. Use the :ref:`retrieve domains operation <domain-operations>` to find the domain ID.

 
**Example: Update domain to require multi-factor authentication for
all users: cURL JSON request**

.. code::  

    $ curl -X -i PUT $IDENTITY_ENDPOINT/RAX-AUTH/domains/$DOMAIN_ID/multi-factor \
         -d '{"RAX-AUTH:multiFactorDomain": {"domainMultiFactorEnforcementLevel": "REQUIRED" }}' \
         -H "Content-type: application/json" \
         -H "X-Auth-Token: $ADMIN_TOKEN" | python -m json.tool 
        

Successful requests return a HTTP `204 No Content` message. To verify
the change, submit a **GET domain by id** request, as shown in the
following example.

 
**Example: Verify domain settings after update: cURL JSON request and response**

.. code::  

    $ curl -X -i GET $IDENTITY_ENDPOINT/RAX-AUTH/domains/$DOMAIN_ID \
         -H "Content-type: application/json" \
         -H "X-Auth-Token: $ADMIN_AUTH_TOKEN" --verbose | python -m json tool
        

.. code::

              GET /v2.0/RAX-AUTH/domains//1234567 HTTP/1.1
              Host: identity.api.rackspacecloud.com
              Accept: */*
              Content-type: application/json
              X-Auth-Token: 12365424dd864ab287a90f06a2069e81

              HTTP/1.1 200 OK
              Content-Type: application/json
              
              {
                "RAX-AUTH:domain": {
                     "domainMultiFactorEnforcementLevel": "REQUIRED",
                     "enabled": true,
                     "id": "6159798"
                }
              }
            

As soon as the domain enforcement level changes to `REQUIRED`, the
Identity service revokes all tokens that were not obtained by using the
multi-factor authentication flow. To regain account access, users who
have not enabled multi-factor authentication can request a scoped
mfa-setup token that they can use to add multi-factor authentication to
their account.

**Next steps**

    -  :ref:`Request a scoped token <auth-request-scoped-mfa-token>`

    -  :ref:`auth-mfa-enabled-account`

    -  :ref:`Customize multi-factor authentication enforcement settings for
       specific users <auth-add-mfa-user-enforcement>`
       


.. _auth-add-mfa-user-enforcement:

Update user-level enforcement for multi-factor authentication
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Rackspace Cloud Identity and user administrators can use customize the
multi-factor enforcement level for specific users by using the update
multi-factor authentication settings operation.

-  Set the enforcement level to `REQUIRED` to require multi-factor
   authentication on the account regardless of the domain level
   enforcement setting.

-  Set the enforcement level to `OPTIONAL` to allow the user to select
   or opt out of multi-factor authentication.

-  Set the enforcement level to `DEFAULT` to allow the user account to
   inherit the domain level enforcement setting.

Administrators can update the user-level enforcement setting from the
API or the Cloud Control Panel. The following figure shows the API work
flow for updating the user enforcement setting with state transitions.

 
**Figure: API workflow for user-level multi-factor authentication enforcement**

.. figure::  ../_images/mfa-user-level-enforce.png
   :alt: API workflow for user-level multi-factor authentication enforcement


The following example assumes the following accounts and credentials: an
authenticated User Administrator account with a valid authentication
token and a user account within the same domain.

 
**Example: Require user to log in by using multi-factor
authentication: cURL JSON request and response**

.. code::  

    $curl -X PUT $IDENTITY_ENDPOINT/users/$USER_ID/RAX-AUTH/multi-factor \
             -d `{"RAX-AUTH:multiFactor": { "userMultiFactorEnforcementLevel": "REQUIRED" }}` \
             -H "Content-type: application/json" \
             -H "X-Auth-Token: $ADMIN_AUTH_TOKEN" --verbose | json
        

.. code:: 

     
           HTTP/1.1 204 No Content
           Vary:  Accept, Accept-Encoding, X-Auth-Token
        

As soon as the user-level enforcement level changes to ``REQUIRED``
or if the value changes to `DEFAULT` and the domain-level
enforcement setting is ``REQUIRED``, the Identity service revokes
all tokens for the user that were not obtained by using the multi-factor
authentication process.

The account user must submit another authentication request to retrieve
a scoped authentication token that allows access to the Identity service
to set up multi-factor authentication on the user account.


.. _auth-request-scoped-mfa-token:

Request a scoped mfa-setup token to set up multi-factor authentication
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If a Rackspace Cloud account requires multi-factor authentication, users
who have not set up and enabled multi-factor authentication get the
following response when they authenticate:

.. code:: 

    HTTP/1.1 403 Forbidden
    Vary:  Accept, Accept-Encoding, X-Auth-Token
    Content-Type: application/json
    {
        "forbidden": {
        "code": 403,
        "message": "User must setup multi-factor"
         }
    }
        

To get account access, the user must request a scoped ``MFA-SETUP``
token that provides limited access to the Identity service for account
configuration.

 
**Example: User authentication request for a scoped mfa-setup token: cURL JSON request and response**

.. code::  

    $ curl -X POST IDENTITY_ENDPOINT/v2.0/tokens \
            -d '{"auth": {"RAX-AUTH:scope": "SETUP-MFA", \
            "passwordCredentials": {"username":"'$USER_ADMIN_USERNAME'", "password":"'$PWD'"}}}'\
            -H "Content-type: application/json" --verbose | python -m json.tool
        

.. code:: 

    HTTP/1.1 200 OK
    Vary:  Accept, Accept-Encoding, X-Auth-Token
    Content-Type: application/json
    Transfer-Encoding: chunked
    Server: Jetty(6.1.25)
    {
    "access": {
        "token":  {
            "RAX-AUTH:authenticatedBy": [
                   "PASSWORD"
                 ],
                "expires": "2014-01-09T15:08:53.645-06:00",
                "id": "449f04aca3594ce38e5b0b18fce6b"
          }
    "user": {
              "RAX-AUTH:defaultRegion": "DFW",
              "id": "161418",
              "name": "mfaTestUser",
              "roles": [
                {
                "description": "User Admin Role.",
                "id": "3",
                "name": "identity:user-admin"
            }
         ]
     }}}
          

.. note:: 
   The service catalog is not returned in the response. The
   ``MFA-SETUP`` token in the response provides users with the limited account
   configuration capabilities as shown in the following figure so that they can 
   set up multi-factor authentication.

 
**Figure: Capabilities available with a scoped mfa-setup token**

.. figure::  ../_images/mfa-setup-token-capabilities.png
   :alt: Capabilities available with a scoped mfa-setup token

After receiving the scoped mfa-setup token, users can export it to an
environment variable as shown in the following example, and use it to
configure their account for multi-factor authentication by using a mobile
phone.

 
**Example: Export scoped token**

.. code::  

    $ export MFA_SETUP_TOKEN="449f04aca3594ce38e5b0b18fce6b"
        

..  note:: 
    As soon as the user has added a multi-factor authentication device to
    their account, the scoped mfa-setup token is revoked, and the user can
    follow the `multi-factor authentication process <auth-mfa-enabled-account>`
    to log in.

