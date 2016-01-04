.. _auth-mfa-manage-accounts:

Manage multifactor-enabled accounts
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Users and administrators can complete the following tasks to manage accounts that use 
multi-factor authentication.

- :ref:`Unlock user account <auth-manage-unlock-account>`
- :ref:`Recover account <auth-manage-recover-account>`
- :ref:`Generate bypass codes <auth-manage-generate-bypass-codes>`
- :ref:`Check multi-factor status on user account <auth-manage-check-mfa-status>`
- :ref:`List multifactor-enabled devices by user id <auth-manage-list-mfa-devices-by-id>`
- :ref:`Disable multi-factor authentication on a user account <auth-manage-disable-mfa-user>` 
- :ref:`Remove multi-factor authentication from user account <auth-remove-mfa-from-user>`


.. Important:: 

    Multi-factor authentication is supported only by Rackspace Cloud
    Identity service version 2.0 or later. After an account is enabled for
    multi-factor authentication, the user cannot authenticate using Identity
    service v1.0 or v1.1.

.. _auth-manage-unlock-account:

Unlock user account
.........................

If your account is locked as a result of failed login attempts, wait 5 minutes and then 
try to authenticate again using the passcode sent to your account. If you are still not 
able to access your account, contact the User administrator to 
:ref:`unlock your account <multifactor-operations>`.


.. _auth-manage-recover-account:

Recover account
................

If you cannot get the multi-factor authentication passcode from the device associated with 
your account or from the saved bypass codes generated for your account, contact Rackspace Support.

.. _Rackspace Support: <http://www.rackspace.com/en-us/support>


.. _auth-manage-generate-bypass-codes:

Generate bypass codes
.......................

Users can submit the following cURL request to 
:ref:`generate bypass codes <multifactor-operations>` 
that can be used in place of the multi-factor authentication passcode if the phone 
associated with the account is not available.

.. code:: 
   
    $ curl $AUTH_ENDPOINT/v2.0/users/$USER_ID/RAX-AUTH/multi-factor/bypass-codes \
           -d '{"RAX-AUTH:bypassCodes":{"validityDuration":"PT30M"}, "numberofCodes": "1"}'
           -H "Content-Type: application/json" \
           -H "X-Auth-Token: $AUTHTOKEN" | python -m json.tool


.. _auth-manage-check-mfa-status:

Check multi-factor status on user account
...........................................

Use the following cURL request to 
:ref: `check the multi-factor authentication status  
on an account <multifactor operations>`. If the account is enabled for multi-factor authentication, 
the user listing includes the `multiFactorEnabled` attribute.

.. code:: 
   
   $ curl $AUTH_ENDPOINT/v2.0/users/$USER_ID \
          -X POST \
          -H "Content-Type: application/json" \
          -H "X-Auth-Token: $AUTHTOKEN" | python -m json.tool
 
.. _auth-manage-list-mfa-devices-by-id:       

List multifactor-enabled devices by user id
.............................................

Users can use the following cURL request to 
:ref:`list multifactor-enabled devices by user id <multifactor-operations>`. 
The operation returns all devices associated with the user account for the purpose 
of multi-factor authentication. 

.. code::

   $ curl $AUTH_ENDPOINT/v2.0/$USER_ID/RAX-AUTH/multi-factor/mobile-phones \
          -X PUT \
          -H "Content-Type: application/json" \
          -H "X-Auth-Token: $AUTHTOKEN" | python -m json.tool
          

.. _auth-manage-disable-mfa-user:

Disable multi-factor authentication on a user account
.......................................................

Use the folowing cURL request to disable (enabled=false) multi-factor for the specified user account.

.. code::

   $ curl $AUTH_ENDPOINT/users/$USER_ID/RAX-AUTH/multi-factor \
           -X PUT \
           -d '{"RAX-AUTH:multiFactor": { "enabled": "false" }}' \
           -H "Content-Type: application/json" \
           -H "X-Auth-Token: $AUTHTOKEN" | python -m json.tool
           

.. _auth-remove-mfa-from-user: 

Remove the multi-factor authentication setting and phone from a user account
..............................................................................

Use the following cURL request to remove multi-factor authentication capabilities from a user account.

.. code::

    $ curl $AUTH_ENDPOINT/users/$USER_ID/RAX-AUTH/multifactor \
           -X DELETE \
           -H "Content-Type: application/json" \
           -H "X-Auth-Token: $AUTHTOKEN" | python -m json.tool
