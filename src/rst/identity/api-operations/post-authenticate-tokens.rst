
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _post-authenticate-tokens:

Authenticate
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /tokens

Authenticates and generates a token.

Authenticates and generates a token.

The Identity service is a ReSTful web service that provides authentication services for the Rackspace Cloud. To gain access, users and administrators can use this POST operation to obtain an authentication token from the Identity service, or generate a new token after a previously issued token has expired.

In subsequent requests to Identity service or other services, you include the authentication token in the HTTP x-header parameter, defined as ``X-Auth-Token`` to verify your identity and permission to perform the requested operation.

Submit the POST token authentication request to the Identity service service endpoint URL with v2.0/tokens supplied as the path and a payload of credentials in the body. User administrators Credentials can include any of the following types:



*  username and API key
*  username, API key, and tenant ID
*  username, API key, and tenant name
*  username and password
*  username, password and tenant ID
*  username, password and tenant name
*  token and tenant ID


You can use whichever valid credentials you prefer. Unless you specify a tenant, the response from the Identity service is not affected by the type of credentials that you use.

.. important::
   If you specify a tenant, the ``Service Catalog`` returned includes only endpoints for the cloud services authorized for that tenant.
   
   

See the following examples to learn about authenticating with different credential types.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |                         |An ``access`` object. A  |
|                          |                         |``token`` object. A      |
|                          |                         |timestamp that indicates |
|                          |                         |when the token was       |
|                          |                         |issued. A timestamp that |
|                          |                         |indicates when the token |
|                          |                         |expires. The             |
|                          |                         |authentication token. In |
|                          |                         |the example, the token   |
|                          |                         |is ``my_id``. A          |
|                          |                         |``tenant`` object. The   |
|                          |                         |description of the       |
|                          |                         |tenant. If not set, this |
|                          |                         |value is ``null``.       |
|                          |                         |Indicates whether the    |
|                          |                         |tenant is enabled or     |
|                          |                         |disabled. The tenant ID. |
|                          |                         |The tenant name. A       |
|                          |                         |``serviceCatalog``       |
|                          |                         |object. One or more      |
|                          |                         |``endpoints`` objects.   |
|                          |                         |Each object shows the    |
|                          |                         |``adminURL``,            |
|                          |                         |``region``,              |
|                          |                         |``internalURL``, ``id``, |
|                          |                         |and ``publicURL`` for    |
|                          |                         |the endpoint. Links for  |
|                          |                         |the endpoint. Endpoint   |
|                          |                         |type. Endpoint name. A   |
|                          |                         |``user`` object, which   |
|                          |                         |shows the ``username``,  |
|                          |                         |``roles_links``, ``id``, |
|                          |                         |``roles``, and ``name``. |
|                          |                         |A ``metadata`` object.   |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |Missing requred          |
|                          |                         |parameters.              |
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |Authentication has       |
|                          |                         |failed. The              |
|                          |                         |authentication token has |
|                          |                         |expired. Use the POST    |
|                          |                         |token operation to get a |
|                          |                         |new token.               |
+--------------------------+-------------------------+-------------------------+
|403                       |Unauthorized             |Permission denied,       |
|                          |                         |adjusting authentication |
|                          |                         |credentials will not     |
|                          |                         |help.                    |
+--------------------------+-------------------------+-------------------------+
|404                       |Unauthorized             |The requested resource   |
|                          |                         |was not found.The        |
|                          |                         |subject token in X-      |
|                          |                         |Subject-Token has        |
|                          |                         |expired or is no longer  |
|                          |                         |available. Use the POST  |
|                          |                         |token request to get a   |
|                          |                         |new token.               |
+--------------------------+-------------------------+-------------------------+


Request
""""""""""""""""








This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|tenantName                |String *(Optional)*      |The tenant name. Both    |
|                          |                         |the ``tenantId`` and     |
|                          |                         |``tenantName``           |
|                          |                         |attributes are optional, |
|                          |                         |but should not be        |
|                          |                         |specified together. If   |
|                          |                         |both attributes are      |
|                          |                         |specified, the server    |
|                          |                         |responds with a ``400``  |
|                          |                         |``Bad Request``.         |
+--------------------------+-------------------------+-------------------------+
|tenantId                  |Uuid *(Optional)*        |The tenant ID. Both the  |
|                          |                         |``tenantId`` and         |
|                          |                         |``tenantName``           |
|                          |                         |attributes are optional, |
|                          |                         |but should not be        |
|                          |                         |specified together. If   |
|                          |                         |both attributes are      |
|                          |                         |specified, the server    |
|                          |                         |responds with a ``400``  |
|                          |                         |``Bad Request``.         |
+--------------------------+-------------------------+-------------------------+
|passwordCredentials       |String *(Optional)*      |A                        |
|                          |                         |``passwordCredentials``  |
|                          |                         |object. To authenticate, |
|                          |                         |you must provide either  |
|                          |                         |a user ID and password   |
|                          |                         |or a token.              |
+--------------------------+-------------------------+-------------------------+
|username                  |String *(Optional)*      |The user name. Required  |
|                          |                         |if you include the       |
|                          |                         |``passwordCredentials``  |
|                          |                         |object. If you do not    |
|                          |                         |provide password         |
|                          |                         |credentials, you must    |
|                          |                         |provide a token.         |
+--------------------------+-------------------------+-------------------------+
|password                  |String *(Optional)*      |The password of the      |
|                          |                         |user. Required if you    |
|                          |                         |include the              |
|                          |                         |``passwordCredentials``  |
|                          |                         |object. If you do not    |
|                          |                         |provide a password       |
|                          |                         |credentials, you must    |
|                          |                         |provide a token.         |
+--------------------------+-------------------------+-------------------------+
|token                     |String *(Optional)*      |A ``token`` object.      |
|                          |                         |Required if you do not   |
|                          |                         |provide password         |
|                          |                         |credentials.             |
+--------------------------+-------------------------+-------------------------+
|id                        |String *(Optional)*      |The token ID. This is a  |
|                          |                         |required field in the    |
|                          |                         |``token`` object.        |
+--------------------------+-------------------------+-------------------------+





**Example Authenticate: XML request**


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <auth>
     <apiKeyCredentials
       xmlns="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"
       username="demoauthor"
       apiKey="aaaaa-bbbbb-ccccc-12345678"/>
     </auth>


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <auth>
     <apiKeyCredentials
       xmlns="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"
       username="demoauthor"
       apiKey="aaaaa-bbbbb-ccccc-12345678"
       tenantId="1100111" />
   </auth>
   	
   
   


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <auth
     xmlns="http://docs.openstack.org/identity/api/v2.0"
     tenantId="1234">
     <passwordCredentials
       username="testuser"
       password="P@ssword1"/>
   </auth>


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <auth xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns="http://docs.openstack.org/identity/api/v2.0">
     <passwordCredentials username="demoauthor" password="theUsersPassword" tenantId="1100111"/>
   </auth>


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <auth xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns="http://docs.openstack.org/identity/api/v2.0"
    tenantId="1100111">
    <token id="xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" />
   </auth>
   
   


.. code::

   <?xml version="1.0" encoding="UTF-8"?>
   <auth xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns="http://docs.openstack.org/identity/api/v2.0"
    tenantName="tenantabc">
    <token id="xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" />
   </auth>
   
   





**Example Authenticate: JSON request**


.. code::

   {
       "auth": {
           "RAX-KSKEY:apiKeyCredentials": {
               "username": "demoauthor",
               "apiKey": "aaaaa-bbbbb-ccccc-12345678"
           }
       }
   }


.. code::

   {
       "auth": {
           "RAX-KSKEY:apiKeyCredentials": {
               "username": "demoauthor",
               "apiKey": "aaaaa-bbbbb-ccccc-12345678"
           },
           "tenantId": "1100111"
       }
   }


.. code::

   {
     "auth": {
       "passwordCredentials": {
         "username": "demoauthor",
         "password": "mypass"
       },
       "tenantId": "1234"
     }
   }


.. code::

   {
       "auth":{
           "passwordCredentials":{
               "username":"demoauthor",
               "password":"theUsersPassword"
           },
           "tenantId": "12345678"
       }
   }


.. code::

   {
       "auth": {
           "tenantId": "1100111",
           "token": {
               "id": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
           }
       }
   }


.. code::

   {
       "auth": {
           "tenantName": "tenantabc",
           "token": {
               "id": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
           }
       }
   }





Response
""""""""""""""""





This table shows the body parameters for the response:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|access                    |String *(Required)*      |An ``access`` object.    |
+--------------------------+-------------------------+-------------------------+
|token                     |String *(Required)*      |A ``token`` object.      |
+--------------------------+-------------------------+-------------------------+
|issued_at                 |String *(Required)*      |A timestamp that         |
|                          |                         |indicates when the token |
|                          |                         |was issued.              |
+--------------------------+-------------------------+-------------------------+
|expires                   |String *(Required)*      |A timestamp that         |
|                          |                         |indicates when the token |
|                          |                         |expires.                 |
+--------------------------+-------------------------+-------------------------+
|id                        |String *(Required)*      |The authentication       |
|                          |                         |token. In the example,   |
|                          |                         |the token is ``my_id``.  |
+--------------------------+-------------------------+-------------------------+
|tenant                    |String *(Required)*      |A ``tenant`` object.     |
+--------------------------+-------------------------+-------------------------+
|description               |String *(Required)*      |The description of the   |
|                          |                         |tenant. If not set, this |
|                          |                         |value is ``null``.       |
+--------------------------+-------------------------+-------------------------+
|enabled                   |Boolean *(Required)*     |Indicates whether the    |
|                          |                         |tenant is enabled or     |
|                          |                         |disabled.                |
+--------------------------+-------------------------+-------------------------+
|id                        |String *(Required)*      |The tenant ID.           |
+--------------------------+-------------------------+-------------------------+
|name                      |String *(Required)*      |The tenant name.         |
+--------------------------+-------------------------+-------------------------+
|serviceCatalog            |String *(Required)*      |A ``serviceCatalog``     |
|                          |                         |object.                  |
+--------------------------+-------------------------+-------------------------+
|endpoints                 |String *(Required)*      |One or more              |
|                          |                         |``endpoints`` objects.   |
|                          |                         |Each object shows the    |
|                          |                         |``adminURL``,            |
|                          |                         |``region``,              |
|                          |                         |``internalURL``, ``id``, |
|                          |                         |and ``publicURL`` for    |
|                          |                         |the endpoint.            |
+--------------------------+-------------------------+-------------------------+
|endpoints_links           |String *(Required)*      |Links for the endpoint.  |
+--------------------------+-------------------------+-------------------------+
|type                      |String *(Required)*      |Endpoint type.           |
+--------------------------+-------------------------+-------------------------+
|name                      |String *(Required)*      |Endpoint name.           |
+--------------------------+-------------------------+-------------------------+
|user                      |String *(Required)*      |A ``user`` object, which |
|                          |                         |shows the ``username``,  |
|                          |                         |``roles_links``, ``id``, |
|                          |                         |``roles``, and ``name``. |
+--------------------------+-------------------------+-------------------------+
|metadata                  |String *(Required)*      |A ``metadata`` object.   |
+--------------------------+-------------------------+-------------------------+







**Example Authenticate: XML response**


.. code::

   





**Example Authenticate: JSON response**


.. code::

   


 For more detailed information about authentication requests and responses with                         see the "Sample Authentication Request and Response" section in the API Developer Guide.

