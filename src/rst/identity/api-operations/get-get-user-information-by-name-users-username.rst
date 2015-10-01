
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-get-user-information-by-name-users-username:

Get user information by name
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /users/{username}

Get detailed account information for a specified user, by user name.

This request returns the following information for each account associated with the specified user name: email address, username, user ID, status, default region, and domain id.

.. note::
   If you authenticated with the user role, you can see only yourself.
   
   If this request is issued by a user holding the admin role ( ``identity:user-admin`` ), the specific user's information is returned only if that user is associated with the same tenant as the requester's ``user-admin`` token.
   
   If this request is issued by a user holding the user role ( ``identity:default`` ), information is returned for only the requester. 
   
   



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |Get user by name: XML    |                         |
|                          |response                 |                         |
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
|X-Auth-Token              |String *(Required)*      |A valid authentication   |
|                          |                         |token with               |
|                          |                         |administrative access.   |
+--------------------------+-------------------------+-------------------------+
|{username}                |String *(Required)*      |The name associated with |
|                          |                         |the user account you     |
|                          |                         |want to look up.         |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




Response
""""""""""""""""





This table shows the body parameters for the response:

+------------------------+-------------+----------------------------------------------------------------+
|Name                    |Type         |Description                                                     |
+========================+=============+================================================================+
|RAX-AUTH:defaultRegion  |String       |Provides the ID for the default regional data center associated |
|                        |*(Optional)* |with the user account, if one exists. Sample values include:    |
|                        |             |``DFW``, ``IAD``, or ``LON``. If a user account is associated   |
|                        |             |with a default region, and the service catalog is available in  |
|                        |             |multiple regions, service requests are directed to the region   |
|                        |             |specified by ``defaultRegion``. For example of services         |
|                        |             |available in multiple regions, see `Sample Authentication       |
|                        |             |Request and Response                                            |
|                        |             |<http://docs.rackspace.com/auth/api/v2.0/auth-client-           |
|                        |             |devguide/content/Sample_Request_Response-d1e64.html>`__ Use the |
|                        |             |`"Update user" <http://docs.rackspace.com/auth/api/v2.0/auth-   |
|                        |             |client-                                                         |
|                        |             |devguide/content/POST_updateUser_v2.0_users__userId__.html>`__  |
|                        |             |API operation to add, remove, or update the defaultRegion       |
|                        |             |setting on an account.                                          |
+------------------------+-------------+----------------------------------------------------------------+
|RAX-AUTH:domainID       |String       |Returns the ID for the domain associated with the user account  |
|                        |*(Optional)* |if one exists. A domain represents an administrative boundary   |
|                        |             |for identity management.                                        |
+------------------------+-------------+----------------------------------------------------------------+
|RAX-                    |Boolean      |Indicates whether the account is enabled for multi-factor       |
|AUTH:multiFactorEnabled |*(Optional)* |authentication.                                                 |
+------------------------+-------------+----------------------------------------------------------------+
|id                      |String       |Returns the ID for the domain associated with the user account  |
|                        |*(Optional)* |if one exists. A domain ID associates the user with a specific  |
|                        |             |domain. The association can be established during account       |
|                        |             |creation and update operations. A domain establishes an         |
|                        |             |administrative boundary for a customer and a container for      |
|                        |             |customer tenants (accounts) and users. Generally, the           |
|                        |             |``domainId`` value matches the value associated with the        |
|                        |             |primary tenant ID for the Rackspace Cloud account.              |
+------------------------+-------------+----------------------------------------------------------------+
|email                   |String       |Returns the email address on the user account if one has been   |
|                        |*(Optional)* |defined.                                                        |
+------------------------+-------------+----------------------------------------------------------------+
|enabled                 |Boolean      |Indicates whether the user can authenticate to the Identity     |
|                        |*(Optional)* |service. If ``enabled="false"``, the user cannot authenticate.  |
|                        |             |Typically, the ``enabled`` setting is set and stored by a       |
|                        |             |backend system integrated with Identity service. To restore     |
|                        |             |account access, work with the Identity service System and user  |
|                        |             |administrators to resolve any issues on the account.            |
+------------------------+-------------+----------------------------------------------------------------+







**Example Get user by name: XML response**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <user xmlns="http://docs.openstack.org/identity/api/v2.0"
         xmlns:ns2="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
         xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
         id="123456" username="jqsmith"
         enabled="true"
         email="john.smith@example.org"
         RAX-AUTH:defaultRegion="DFW"
         RAX-AUTH:domainId="5830280"
         RAX-AUTH:multiFactorEnabled="true" >
   </user>





**Example Get user by name: JSON response**


.. code::

   {
     "user": {
     
       "id": "123456",
       "username": "jqsmith",
       "email": "john.smith@example.org",
       "enabled": true,
       "RAX-AUTH:defaultRegion":"DFW",
       "RAX-AUTH:domainId":"5830280",
       "RAX-AUTH:multiFactorEnabled": true
       
     }
   }




