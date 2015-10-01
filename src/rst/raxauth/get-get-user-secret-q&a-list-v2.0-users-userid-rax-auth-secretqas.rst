
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-get-user-secret-q&a-list-v2.0-users-userid-rax-auth-secretqas:

Get user secret Q&A list
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v2.0/users/{userId}/RAX-AUTH/secretqas

Returns the list of secret questions and answers for a user account.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |The request succeeded.   |
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

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{userId}                  |String *(Required)*      |The unique, system-      |
|                          |                         |generated user ID for an |
|                          |                         |account.                 |
+--------------------------+-------------------------+-------------------------+
|X-Auth-Token              |String *(Required)*      |A valid authentication   |
|                          |                         |token                    |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




Response
""""""""""""""""





This table shows the body parameters for the response:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|questions                 |Questions *(Required)*   |An object that contains  |
|                          |                         |the collection of secret |
|                          |                         |questions that can be    |
|                          |                         |added to user accounts.  |
+--------------------------+-------------------------+-------------------------+
|question                  |Question *(Required)*    |An object that contains  |
|                          |                         |the ID and text for a    |
|                          |                         |secret question.         |
+--------------------------+-------------------------+-------------------------+
|id                        |String *(Required)*      |The unique, system-      |
|                          |                         |generated ID assigned    |
|                          |                         |when the question was    |
|                          |                         |created.                 |
+--------------------------+-------------------------+-------------------------+
|question                  |String *(Required)*      |The text for the         |
|                          |                         |question.                |
+--------------------------+-------------------------+-------------------------+







**Example Get user secret Q&A list: XML response**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <secretqas
       xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
       xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
       xmlns:atom="http://www.w3.org/2005/Atom" 
       xmlns:identity="http://docs.openstack.org/identity/api/v2.0">
       <secretqa answer="Himalayas" id="1" question="What is the location of a dream vacation?"/>
   </secretqas>





**Example Get user secret Q&A list: JSON response**


.. code::

   {
      "RAX-AUTH:secretqas": [
        {
          "id": "1",
          "answer": "Himalayas",
          "question": "What is the location of a dream vacation?"
        }
      ]
   }




