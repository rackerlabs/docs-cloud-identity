
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _delete-revoke-token-tokens-tokens-tokenid:

Revoke Token
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    DELETE /tokens/tokens/{tokenId}

Revoke token.

This call revokes a token, returning a ``204``. message if successful. If the token and ``404`` if token in URI is invalid. 



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|204                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|404                       |Unauthorized             |The requested resource   |
|                          |                         |was not found.The        |
|                          |                         |subject token in X-      |
|                          |                         |Subject-Token has        |
|                          |                         |expired or is no longer  |
|                          |                         |available. Use the POST  |
|                          |                         |token request to get a   |
|                          |                         |new token.               |
+--------------------------+-------------------------+-------------------------+


Request
""""""""""""""""




This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|tokenID                   |Uuid *(Required)*        |The ID for the token     |
|                          |                         |that you want to delete. |
+--------------------------+-------------------------+-------------------------+
|X-Auth-Token              |String *(Required)*      |A valid administrator    |
|                          |                         |authentication token.    |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




Response
""""""""""""""""






This operation does not return a response body.




