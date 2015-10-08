.. _auth-resp-token-resource:

Token resource: authentication response attributes
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The token object supplies a scoped authentication token that customers
and processes can use to access Rackspace Cloud services for the
specified tenant. Token scope is determined by tenant and user role
assignments for the authenticated user. Responses can be in 
JSON or XML format as shown in the following examples. For details, see the 
:ref:token object attribute descriptions <auth-resp-token-obj-attribs> in
the table following the examples.

.. _auth-resp-token-obj-json:
 
**Example: Authentication response token object in JSON format**

.. code::  

        {
            "token": {
                "id": "d74f592f986e4d6e995853ccf0123456",
                "expires": "2015-06-05T16:24:57.637Z",
                "tenant": {
                    "id": "123456",
                    "name": "123456"
                },
                "RAX-AUTH:authenticatedBy": [
                    "APIKEY"
                ]
        }
            


.. _auth-resp-token-obj-xml:

**Example: Authentication response token object in XML format**

.. code::  

            
        <token id="abcdef123ghi4j5k67m8910n12op3qrs" expires="2014-12-05T17:36:38.662Z">
            <tenant id="123456" name="123456"/>
            <rax-auth:authenticatedBy>
                <rax-auth:credential>APIKEY</rax-auth:credential>
            </rax-auth:authenticatedBy>
        </token>
        
.. _auth-resp-token-obj-attribs:         

**Table:  Authentication response: Token object attributes descriptions** 

+-----------------+-----------+-------------------------------------------------+
| Attribute       | Type      | Description                                     |
+=================+===========+=================================================+
| `id`            | String    | The unique, system-assigned ID for the          |
|                 |           | authentication token. The token ID can be       |
|                 |(Optional) | presented to a service as evidence of           |
|                 |           | authentication. Tokens are valid for a finite   |
|                 |           | duration; a token's default lifespan is         |
|                 |           | twenty-four hours. In the authentication        |
|                 |           | response example, the token is                  |
|                 |           | `aaaaa-bbbbb-ccccc-dddd`.                       |
+-----------------+-----------+-------------------------------------------------+
| `expires`       | String    | A timestamp that indicates when the token       |
|                 |           | expires.                                        |
|                 |(Required) |                                                 |
|                 |           | By default, a token id expires 24-hours after   |
|                 |           | being generated, unless the token is revoked    |
|                 |           | before it expires. Clients are encouraged to    |
|                 |           | cache the token until it expires. After the     |
|                 |           | token expires, client users and applications    |
|                 |           | must re-authenticate to get a new token.        |
+-----------------+-----------+-------------------------------------------------+
| `RAX-AUTH:Auth  | String    | Indicates the type of authentication            |
| enticatedBy`    |           | credentials used to generate the token, which   |
|                 |(Required) | can include the following values:               |
|                 |           |                                                 |
|                 |           | -  `APIKEY` for the API key assigned to the     |
|                 |           |    user account.                                |
|                 |           |                                                 |
|                 |           | -  `PASSCODE` sent to a mobile phone            |
|                 |           |    associated with a user account.              |
|                 |           |                                                 |
|                 |           | -  `PASSWORD` for Rackspace Cloud account       |
|                 |           |    password.                                    |
|                 |           |                                                 |
|                 |           | -  `FEDERATED` if the user authenticated        |
|                 |           |    through a trusted third-party Identity       |
|                 |           |    provider.                                    |
|                 |           |                                                 |
|                 |           |                                                 |
|                 |           |                                                 |
+-----------------+-----------+-------------------------------------------------+

