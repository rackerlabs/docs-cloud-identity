
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-get-user-credentials-v2.0-users-userid-os-ksadm-credentials:

Get user credentials
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v2.0/users/{userId}/OS-KSADM/credentials

Gets user credentials.

Get user credentials.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200 203                   |OK                       |Request completed        |
|                          |                         |successfully.            |
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
|503                       |Service Fault            |Service is not available.|
+--------------------------+-------------------------+-------------------------+


Request
""""""""""""""""




This table shows the URI parameters for the request:

+-------------------------+---------------------------+------------------------+
|Name                     |Type                       |Description             |
+=========================+===========================+========================+
|X-Auth-Token             |String *(Required)*        |You need a valid admin  |
|                         |                           |token for access.       |
+-------------------------+---------------------------+------------------------+
|{userId}                 |String *(Required)*        |The ID of the user for  |
|                         |                           |which you want to       |
|                         |                           |perform the request.    |
+-------------------------+---------------------------+------------------------+
|{credentialType}         |Extensiblecredentialstype  |A credential type       |
|                         |*(Required)*               |                        |
+-------------------------+---------------------------+------------------------+





This operation does not accept a request body.




Response
""""""""""""""""










**Example Get user credentials: XML response**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
    <passwordCredentials xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
     xmlns="http://docs.openstack.org/identity/api/v2.0" username="test_user" password="resetpass"/>





**Example Get user credentials: JSON response**


.. code::

   {
       "passwordCredentials": {
           "username": "test_user",
           "password": "resetpass"
       }
   }




