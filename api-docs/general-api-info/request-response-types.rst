==========================
Request and response types
==========================

The |apiservice| supports both the JSON and XML data serialization formats.

The request format is specified by using the ``Content-Type`` header and is
required for operations that have a request body.

The response format can be specified in requests either by using the ``Accept``
header or adding an ``.xml`` or ``.json`` extension to the request URI. A
response  can be serialized using a format that is different from the request.
If no response format is specified, JSON is the default. If conflicting
formats are specified by using both an ``Accept`` header and a query
extension, the query extension takes precedence.

.. list-table:: **JSON and XML response formats**
   :widths: 10 20 10 10
   :header-rows: 1

   * - Format
     - Accept header
     - Query extension
     - Default
   * - JSON
     - application/json
     - .json
     - Yes
   * - XML
     - application/xml
     - .xml
     - No



**Content-Type header syntax**

The Content-Type header is required for API operations that have a request
body.

    .. code::

        Content-Type: application/format

The ``format`` type can be either ``json`` or ``xml``.



Accept header syntax
~~~~~~~~~~~~~~~~~~~~

For the Accept header, you can use the following syntax or the *Query
extension* syntax.

    .. code::

        Accept: application/<format>

Replace *format* with the desired value: ``json`` or ``xml``.

For the Query extension syntax, add an ``.xml`` or ``.json`` extension to the
request URI. For example, the ``.xml``  extension in the following URI request
specifies that the response body be returned in XML format.

    .. code::

        POST /v2/tokens.xml

If you specify different formats for the Accept header and the query
extension, the format specified in the query extension takes precedence.
For example, if the query extension is ``.xml`` and the Accept header
specifies ``application/json``, the response is returned in xml format.

You can serialize a response in a different format from the request
format as shown in the following examples
:ref:`JSON <auth-req-header-json-example>`
and :ref:`XML <auth-req-header-xml-example>`.

In these examples, the request body is in JSON format with the Accept header
specified as XML. When the request is submitted, the response is returned in
XML format.

 
.. _auth-req-header-json-example:

**Example: Authentication Request with Headers: JSON**

.. code::

    &amp;lt; &amp;lt; POST /v2.0/tokens HTTP/1.1
    Host: identity.api.rackspacecloud.com
    Content-Type: application/json
    Accept: application/xml

    {
      "auth": {
        "passwordCredentials": {
          "username": "demoauthor",
          "password": "mypass"
        },
        "tenantId": "1234"
      }
    }


.. _auth-req-header-xml-example:

**Example: Response with Headers: XML**

.. code::

    HTTP/1.1 200 OK
    Date: Sun, 29 Jun 2014 03:35:05 GMT
    Content-Type: application/xml
    Content-Length: 1060
    Connection: keep-alive
    vary: Accept, Accept-Encoding, X-Auth-Token

    <access xmlns:atom="http://www.w3.org/2005/Atom"
    xmlns:rax-auth="http://docs.rackspace.com/identity/api/ext/RAX-AUTH/v1.0"
    xmlns="http://docs.openstack.org/identity/api/v2.0"
    xmlns:ns4="http://docs.rackspace.com/identity/api/ext/RAX-KSGRP/v1.0"
    xmlns:rax-ksqa="http://docs.rackspace.com/identity/api/ext/RAX-KSQA/v1.0"
    xmlns:os-ksadm="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
    xmlns:rax-kskey="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"
    xmlns:os-ksec2="http://docs.openstack.org/identity/api/ext/OS-KSEC2/v1.0">
         <token id="yyyyxxxaxxxxyyyyyyxxxxxxxyyyyy" expires="2014-06-29T21:09:34.085Z">
              <rax-auth:authenticatedBy>
                   <rax-auth:credential>PASSWORD</rax-auth:credential>
              </rax-auth:authenticatedBy>
         </token>
         <user name="demoauthor" rax-auth:defaultRegion="DFW" rax-auth:federated="false">
              <roles>
                   <role id="3" name="user:admin" description="User Admin Role."/>
              </roles>
         </user>
         <serviceCatalog/>
    </access>
