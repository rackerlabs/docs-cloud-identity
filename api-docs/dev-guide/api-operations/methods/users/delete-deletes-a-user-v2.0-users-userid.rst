.. _delete-a-user-v2.0:

Delete a user
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    DELETE /v2.0/users/{userId}

Deletes a user.

Rackspace Cloud account administrators (``identity:user-admin``) can use the Delete user 
operation to remove a user from a Rackspace Cloud account. Administrators can only delete 
user accounts that are assigned the user role (``identity:default``) with the same tenant 
id as the Administrator account.

To delete a user, specify the user ID in the request. If you know the user name but not id, 
use the :ref:`List users <get-list-users-v2.0>` operation to look up account information by name.

.. warning::

   Don’t delete the wrong user! Before submitting the Delete request, use the List 
   users or :ref:`Get user by id <get-user-by-id-v2.0>` operation to review the user 
   account information and confirm that you are working with the correct account.
   
This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|204                       |No content               |The server fulfilled the |
|                          |                         |request but does not     |
|                          |                         |need to return a body.   |
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

This table shows the header and URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|X-Auth-Token              |Header                   |A valid admin            |
|                          |String *(Required)*      |authentication token.    |
+--------------------------+-------------------------+-------------------------+
|{userId}                  |URI String               |A user ID assigned by    |
|                          |String *(Required)*      |system when user is      |
|                          |                         |added.                   |
+--------------------------+-------------------------+-------------------------+



**Example:  Delete user HTTP request header: XML**


.. code::

   DELETE /v2.0/users/123456 HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/xml
   Content-type: application/xml
   X-Auth-Token: eaf8345057414cd397d0543123456789
   
   
**Example:  Delete user HTTP request header: JSON**


.. code::

   POST /v2.0/users/123456 HTTP/1.1
   Host: identity.api.rackspacecloud.com
   Accept: application/json
   Content-type: application/json
   X-Auth-Token: eaf8345057414cd397d0543123456789


This operation does not accept a request body.

Response
""""""""""""""""

This operation does not return a response body.




