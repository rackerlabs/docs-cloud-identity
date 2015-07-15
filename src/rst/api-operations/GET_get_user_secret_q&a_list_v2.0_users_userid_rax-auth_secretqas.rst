=============================================================================
Get User Secret Q&A List -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Get User Secret Q&A List
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_get_user_secret_q&a_list_v2.0_users_userid_rax-auth_secretqas.rst#request>`__
`Response <GET_get_user_secret_q&a_list_v2.0_users_userid_rax-auth_secretqas.rst#response>`__

.. code-block:: javascript

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
|                          |                         |the values of            |
|                          |                         |someelements are invalid.|
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
|                          |                         |requested                |
|                          |                         |resource.Submit a        |
|                          |                         |request to your account  |
|                          |                         |administrator to         |
|                          |                         |determine how to gain    |
|                          |                         |access.                  |
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
|404                       |Not Found                |The requested resource   |
|                          |                         |was not found.           |
+--------------------------+-------------------------+-------------------------+


Request
^^^^^^^^^^^^^^^^^

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{userId}                  |string *(Required)*      |The unique, system-      |
|                          |                         |generated user ID for an |
|                          |                         |account.                 |
+--------------------------+-------------------------+-------------------------+
|X-Auth-Token              |string *(Required)*      |A valid authentication   |
|                          |                         |token                    |
+--------------------------+-------------------------+-------------------------+








Response
^^^^^^^^^^^^^^^^^^


This table shows the body parameters for the response:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|questions                 |RAX-AUTH:Questions       |An object that contains  |
|                          |*(Required)*             |the collection of secret |
|                          |                         |questions that can be    |
|                          |                         |added to user accounts.  |
+--------------------------+-------------------------+-------------------------+
|question                  |RAX-AUTH:Question        |An object that contains  |
|                          |*(Required)*             |the ID and text for a    |
|                          |                         |secret question.         |
+--------------------------+-------------------------+-------------------------+
|id                        |string *(Required)*      |The unique, system-      |
|                          |                         |generated ID assigned    |
|                          |                         |when the question was    |
|                          |                         |created.                 |
+--------------------------+-------------------------+-------------------------+
|question                  |string *(Required)*      |The text for the         |
|                          |                         |question.                |
+--------------------------+-------------------------+-------------------------+





**Example Get User Secret Q&A List: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <secretqas
        xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
        xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
        xmlns:atom="http://www.w3.org/2005/Atom" 
        xmlns:identity="http://docs.openstack.org/identity/api/v2.0">
        <secretqa answer="Himalayas" id="1" question="What is the location of a dream vacation?"/>
    </secretqas>


**Example Get User Secret Q&A List: JSON request**


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

