
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _post-add-a-mobile-phone-v2.0-users-userid-rax-auth-multi-factor-mobile-phones:

Add a mobile phone
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /v2.0/users/{userId}/RAX-AUTH/multi-factor/mobile-phones

Adds a mobile phone number to the specified user account to support multi-factor authentication.

The operation updates the specified user account with a phone number for multi-factor authentication. The same phone number can be associated with multiple accounts.

Add mobile phone: cURL request

 ``$ curl $AUTH_URL/v2.0/users/$USER_ID/RAX-AUTH/multi-factor/mobile-phones  \        -X POST \        -H "Content-Type: application/json" \        -H "X-Auth-Token: $AUTH_TOKEN"        -d '{"RAX-AUTH:mobilePhone": { "number": "+1 210-312-4600" }}' \         | python -m json.tool`` .. note::
   This example assumes that the endpoint URL, user ID, and authentication token have been exported to these environment variables: ``AUTH_URL, USER_ID``, and ``AUTH_TOKEN``.
   
   



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|201                       |Success                  |The mobile phone has     |
|                          |                         |been added to the user   |
|                          |                         |account.                 |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |The request is missing   |
|                          |                         |one or more elements, or |
|                          |                         |the values of some       |
|                          |                         |elements are invalid.    |
|                          |                         |For example, you might   |
|                          |                         |get this error if the    |
|                          |                         |phone number format is   |
|                          |                         |incorrect.               |
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |You are not authorized   |
|                          |                         |to complete this         |
|                          |                         |operation.               |
+--------------------------+-------------------------+-------------------------+
|403                       |Forbidden                |You do not have          |
|                          |                         |permission to access the |
|                          |                         |requested resource. This |
|                          |                         |error might be returned  |
|                          |                         |if the user ID is        |
|                          |                         |invalid or if it does    |
|                          |                         |not exist.               |
+--------------------------+-------------------------+-------------------------+
|500                       |Service Fault            |The service is not       |
|                          |                         |available.               |
+--------------------------+-------------------------+-------------------------+


Request
""""""""""""""""




This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{userId}                  |String *(Required)*      |The unique, system-      |
|                          |                         |generated user ID for an |
|                          |                         |account.                 |
+--------------------------+-------------------------+-------------------------+
|X-Auth-Token              |String *(Required)*      |A valid authentication   |
|                          |                         |token.                   |
+--------------------------+-------------------------+-------------------------+





This table shows the body parameters for the request:

+------------------------+------------------------+----------------------------+
|Name                    |Type                    |Description                 |
+========================+========================+============================+
|number                  |String *(Required)*     |The phone number for the    |
|                        |                        |mobile phone you want to    |
|                        |                        |add in `E.123 format        |
|                        |                        |<https://www.itu.int/rec/T- |
|                        |                        |REC-E.123-200102-I/en>`__.  |
|                        |                        |+1 235-435-623 or +44 42    |
|                        |                        |1123 4567 for example.      |
+------------------------+------------------------+----------------------------+





**Example Add a mobile phone: XML request header**


.. code::

   POST /v2.0/users/10d2c2d0f3b644b9abea0d9fe8123456/RAX-AUTH/multi-factor/mobile-phones HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/xml
   X-Auth-Token: 6cac79a5c16343abb7c41b6bee123456
   Content-type: application/xml
   





**Example Add a mobile phone: XML request**


.. code::

   POST /v2.0/users/10d2c2d0f3b644b9abea0d9fe8123456/RAX-AUTH/multi-factor/mobile-phones HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/xml
   X-Auth-Token: 6cac79a5c16343abb7c41b6bee123456
   Content-type: application/xml
   
   <?xml version="1.0" encoding="UTF-8"?>
   <RAX-AUTH:mobilePhone number="+1 210-312-4600"
        xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
        xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
        xmlns:atom="http://www.w3.org/2005/Atom" xmlns:identity="http://docs.openstack.org/identity/api/v2.0"/>
   





**Example Add mobile phone: JSON request header**


.. code::

   POST /v2.0/users/10d2c2d0f3b644b9abea0d9fe8123456/RAX-AUTH/multi-factor/mobile-phones HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/xml
   X-Auth-Token: 6cac79a5c16343abb7c41b6bee123456
   Content-type: application/json
   





**Example Add mobile phone: JSON request**


.. code::

   {
       "RAX-AUTH:mobilePhone": {
       "number": "+1 210-312-4600"
       }
    }
   





Response
""""""""""""""""





This table shows the body parameters for the response:

+------------------------+------------------------+----------------------------+
|Name                    |Type                    |Description                 |
+========================+========================+============================+
|id                      |String *(Required)*     |The unique, system-         |
|                        |                        |generated ID assigned to    |
|                        |                        |the phone added to the      |
|                        |                        |account.                    |
+------------------------+------------------------+----------------------------+
|verified                |Boolean *(Optional)*    |A Boolean value that        |
|                        |                        |indicates whether the phone |
|                        |                        |can be used to authenticate |
|                        |                        |to the Identity service.    |
|                        |                        |Phones can be verified by   |
|                        |                        |using the Send verification |
|                        |                        |code and Verify device      |
|                        |                        |operations.                 |
+------------------------+------------------------+----------------------------+
|number                  |String *(Required)*     |The phone number added to   |
|                        |                        |the user account for use    |
|                        |                        |with multi-factor           |
|                        |                        |authentication services.    |
|                        |                        |`E.123 format               |
|                        |                        |<https://www.itu.int/rec/T- |
|                        |                        |REC-E.123-200102-I/en>`__.  |
|                        |                        |+1 235-435-623 or +44 42    |
|                        |                        |1123 4567 for example.      |
+------------------------+------------------------+----------------------------+







**Example Add a mobile phone: XML response**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <mobilePhone id="e0de732f1b1c4fec9d4f266326123456" verified="false" number="+1 210-312-4600"
        xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
        xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
        xmlns:atom="http://www.w3.org/2005/Atom" xmlns:identity="http://docs.openstack.org/identity/api/v2.0"/>
   





**Example Add a moble phone: JSON response**


.. code::

   {
       "RAX-AUTH:mobilePhone": {
           "id": "e0de732f1b1c4fec9d4f266326123456",
           "number": "+1 210-312-4600"
       }
   }




