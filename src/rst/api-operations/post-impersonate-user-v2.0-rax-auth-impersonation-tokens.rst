
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _post-impersonate-user-v2.0-rax-auth-impersonation-tokens:

Impersonate user
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /v2.0/RAX-AUTH/impersonation-tokens

Impersonates a specific user.

Authenticated Rackers that have the Identity admin role can use this operation to impersonate a user. When you submit the request, include the ``username`` for the account user that you want to impersonate.

You can also specify the number of seconds you want the impersonation to remain valid. For example, ``< expire-in-seconds > 10800 < /expire-in-seconds >`` asks for 10,800 seconds (180 minutes, or 3 hours) of impersonation. Whether or not you requested a specific expiration time, your impersonation period will be limited. The response to your impersonation request returns the timestamp for the token expiration.



*  In an impersonation request, express your request for time as a number of seconds.
*  In an impersonation response, the expiration time granted to you is expressed as a timestamp.


A successful impersonation request returns a token and an expiration time for that token. You can impersonate ``username`` by supplying that token in other requests, until the token expires.



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
""""""""""""""""




This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|X-Auth-Token              |String *(Required)*      |A valid authentication   |
|                          |                         |token for the            |
|                          |                         |impersonator             |
+--------------------------+-------------------------+-------------------------+





This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|user                      |String *(Required)*      |Specify the username     |
+--------------------------+-------------------------+-------------------------+
|RAX-AUTH:federatedIdp     |String *(Optional)*      |Specifies the URI of the |
|                          |                         |Identity provider used   |
|                          |                         |to authenticate user.    |
+--------------------------+-------------------------+-------------------------+
|expire-in-seconds         |String *(Optional)*      |Specifies the number of  |
|                          |                         |seconds that the         |
|                          |                         |impersonation remains    |
|                          |                         |valid.                   |
+--------------------------+-------------------------+-------------------------+





**Example Impersonate user: XML request**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <impersonation
       xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
       xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
       xmlns:atom="http://www.w3.org/2005/Atom" 
       xmlns:identity="http://docs.openstack.org/identity/api/v2.0">
       <user username="john.smith"/>
       <expire-in-seconds>10800</expire-in-seconds>
   </impersonation>





**Example Impersonate user: JSON request**


.. code::

   {
     "RAX-AUTH:impersonation": {
         "user": {
             "username": "john.smith"
         },
         "expire-in-seconds": 10800
     }
   }  





**Example Impersonate a Federated user: XML request**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <impersonation
       xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
       xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
       xmlns:atom="http://www.w3.org/2005/Atom" 
       xmlns:identity="http://docs.openstack.org/identity/api/v2.0"
       xmlns:RAX-AUTH="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0">
       <user username="john.smith" RAX-AUTH:federatedIdp="http://test.rackspace.com"/>
       <expire-in-seconds>10800</expire-in-seconds>
   </impersonation>





**Example Impersonate a Federated user: JSON request**


.. code::

   {
     "RAX-AUTH:impersonation": {
         "user": {
             "username": "john.smith",
             "RAX-AUTH:federatedIdp": "http://test.rackspace.com"
         },
         "expire-in-seconds": 10800
     }
   }  





Response
""""""""""""""""










**Example Impersonate user: XML response**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <access xmlns="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
       xmlns:OS-KSADM="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
       xmlns:atom="http://www.w3.org/2005/Atom" 
       xmlns:identity="http://docs.openstack.org/identity/api/v2.0">
       <token expires="2011-09-08T07:00:00.000-05:00" 
           id="xxx-yyy-zzz-kwejKId893KJDKJKSKJSM"/>
   </access>





**Example Impersonate user: JSON response**


.. code::

   {
     "access": {
         "token": {
             "expires": "2011-09-08T07:00:00.000-05:00",
             "id": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
          }
     }
   }




