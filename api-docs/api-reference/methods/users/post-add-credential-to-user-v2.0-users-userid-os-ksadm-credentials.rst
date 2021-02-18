.. _post-add-credential-to-user-v2.0-osksadm:

Add credential to user
~~~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /v2.0/users/{userId}/OS-KSADM/credentials

.. note::

    This Add API-key credentials to a user operation is deprecated.
    Instead, use :ref:`Reset API Key<post-reset-api-key-for-user-v2.0>`

Use this API operation to add a password credential to a user account.

To add a password, specify the user's ID in the request. If you know the
user's name but not the user's ID, use :ref:`List users <get-list-users-v2.0>`
operation  to find the ID.

This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|201                       |Created                  |The request has been     |
|                          |                         |fulfilled. The           |
|                          |                         |credential has been      |
|                          |                         |added.                   |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |The request is missing   |
|                          |                         |one or more elements, or |
|                          |                         |the values of some       |
|                          |                         |elements are invalid.    |
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |You are not authorized   |
|                          |                         |to complete this         |
|                          |                         |operation. This error    |
|                          |                         |can occur if the request |
|                          |                         |is submitted with an     |
|                          |                         |invalid authentication   |
|                          |                         |token.                   |
+--------------------------+-------------------------+-------------------------+
|403                       |Forbidden                |The request was valid,   |
|                          |                         |but the server is        |
|                          |                         |refusing to respond      |
|                          |                         |because you do not have  |
|                          |                         |permission to access the |
|                          |                         |requested resource.      |
|                          |                         |Submit a request to your |
|                          |                         |account administrator to |
|                          |                         |determine how to gain    |
|                          |                         |access.                  |
+--------------------------+-------------------------+-------------------------+
|404                       |Not Found                |The requested resource   |
|                          |                         |was not found.           |
+--------------------------+-------------------------+-------------------------+
|405                       |Invalid Method           |The method specified in  |
|                          |                         |the request is not valid |
|                          |                         |for the resource         |
|                          |                         |identified in the        |
|                          |                         |request URI.             |
+--------------------------+-------------------------+-------------------------+
|413                       |Over Limit               |The number of items      |
|                          |                         |returned is above the    |
|                          |                         |allowed limit.           |
+--------------------------+-------------------------+-------------------------+
|415                       |Bad Media Type           |Bad media type. This may |
|                          |                         |result if the wrong      |
|                          |                         |media type is used in    |
|                          |                         |the API request. Check   |
|                          |                         |the content-type and     |
|                          |                         |accept headers included  |
|                          |                         |in the request.          |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Fault            |Service is not available.|
+--------------------------+-------------------------+-------------------------+


Request
-------

This table shows the header and URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|X-Auth-Token              |Header                   |A valid admin            |
|                          |String *(Required)*      |authentication token.    |
+--------------------------+-------------------------+-------------------------+
|{userId}                  |URI                      |A user ID assigned by    |
|                          |String *(Required)*      |system when user is      |
|                          |                         |added.                   |
+--------------------------+-------------------------+-------------------------+


This operation does not accept a request body.


**Example:  Add credential to user: XML request**

.. code::

   <?xml version="1.0" encoding="UTF-8"?>
    <passwordCredentials xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
     xmlns="http://docs.openstack.org/identity/api/v2.0" username="test_user" password="resetpass"/>



**Example:  Add credential to user: JSON request**


.. code::

   {
       "passwordCredentials": {
           "username": "test_user",
           "password": "resetpass"
       }
   }

Response
--------

**Example:  Add credential to user: JSON response**


.. code::

   {
       "passwordCredentials": {
           "username": "test_user",
           "password": "resetpass"
       }
   }


**Example:  Add credential to user: XML response**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
    <passwordCredentials xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
     xmlns="http://docs.openstack.org/identity/api/v2.0" username="test_user" password="resetpass"/>
