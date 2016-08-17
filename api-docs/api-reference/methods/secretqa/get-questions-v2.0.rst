.. _get-questions-v2.0:

Get questions
~~~~~~~~~~~~~~

.. code::

    GET /v2.0/RAX-AUTH/secretqa/questions

Returns a list of secret questions that can be added to user accounts.

The list includes secret questions and associated IDs required to manage
questions by  using the Identity service API. questions.


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
-------

This table shows the header parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|X-Auth-Token              |Header                   |A valid admin            |
|                          |String *(Required)*      |authentication token.    |
+--------------------------+-------------------------+-------------------------+


This operation does not accept a request body.



Response
--------

**Example:  Get questions response: XML**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <rax-auth:questions xmlns:atom="http://www.w3.org/2005/Atom" \
        xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0" \
        xmlns="http://docs.openstack.org/identity/api/v2.0" \
        xmlns:ns4="http://docs.rackspace.com/identity/api/ext/RAX-KSGRP/v1.0" \
        xmlns:rax-ksqa="http://docs.rackspace.com/identity/api/ext/RAX-KSQA/v1.0" \
        xmlns:os-ksadm="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0" \
        xmlns:rax-kskey="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0" \
        xmlns:os-ksec2="http://docs.openstack.org/identity/api/ext/OS-KSEC2/v1.0">
        <rax-auth:question id="6" question="What is your pass phrase?"/>
        <rax-auth:question id="5" question="Who let the dogs out?"/>
        <rax-auth:question id="4" question="What is your favorite color?"/>
        <rax-auth:question id="3" question="What is your favorite book?"/>
        <rax-auth:question id="2" question="Where is the best place to live?"/>
        <rax-auth:question id="1" question="What is the location of your dream vacation?"/>
        <rax-auth:question id="1017" question="What's your fathers name?"/>
   </rax-auth:questions>


**Example:  Get questions response: JSON**


.. code::

   {
     "RAX-AUTH:questions": [
       {
               "id": "6",
               "question": "What is your pass phrase?"
           },
           {
               "id": "5",
               "question": "Who let the dogs out?"
           },
           {
               "id": "4",
               "question": "What is your favorite color?"
           },
           {
               "id": "3",
               "question": "What is your favorite book?"
           },
           {
               "id": "2",
               "question": "Where is the best place to live?"
           },
           {
               "id": "1",
               "question": "What is the location of your dream vacation?"
           }
     ]
   }
