=============================================================================
Create A Secret Question -  Rackspace Cloud Identity Developer Guide - API v2.0
=============================================================================

Create A Secret Question
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <POST_create_a_secret_question_v2.0_rax-auth_secretqa_questions.rst#request>`__
`Response <POST_create_a_secret_question_v2.0_rax-auth_secretqa_questions.rst#response>`__

.. code-block:: javascript

    POST /v2.0/RAX-AUTH/secretqa/questions

Creates a secret question that can be added to user accounts.

Identity administrators can create security questions for account verification. When the question is created, the Identity service assigns a unique question ID and returns the value in the LOCATION field of the response header. You need the ID when you submit API requests to update, delete, or assign the secret question to a user account.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|201                       |                         |Location of the URI for  |
|                          |                         |the newly-created        |
|                          |                         |question that includes   |
|                          |                         |the question ID assigned |
|                          |                         |by the Identity service. |
+--------------------------+-------------------------+-------------------------+
|409                       |Conflict                 |The request could not be |
|                          |                         |completed due to a       |
|                          |                         |conflict with the        |
|                          |                         |current state of the     |
|                          |                         |resource.                |
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
|415                       |Bad Media Type           |Bad media type. This may |
|                          |                         |result if the wrong      |
|                          |                         |media type is used in    |
|                          |                         |the API request. Check   |
|                          |                         |the content-type and     |
|                          |                         |accept headers included  |
|                          |                         |in the request.          |
+--------------------------+-------------------------+-------------------------+


Request
^^^^^^^^^^^^^^^^^

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|X-Auth-Token              |string *(Required)*      |A valid authentication   |
|                          |                         |token                    |
+--------------------------+-------------------------+-------------------------+





This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|question                  |string *(Required)*      |Specifies the text for a |
|                          |                         |secret question.         |
+--------------------------+-------------------------+-------------------------+





**Example Create A Secret Question: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <question question="What is the location of a dream vacation?"
         xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
         xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
         xmlns:atom="http://www.w3.org/2005/Atom" xmlns:identity="http://docs.openstack.org/identity/api/v2.0"/>
    


**Example Create A Secret Question: JSON request**


.. code::

    {
      "RAX-AUTH:question": {
        "question": "What is the location of a dream vacation?"
      }
    }


Response
^^^^^^^^^^^^^^^^^^




