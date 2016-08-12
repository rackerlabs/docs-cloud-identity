=====================
Paginated collections
=====================

To reduce load on the service, list operations return a maximum number
of items at a time. The maximum number of items returned is determined
by the Identity service configuration. To navigate the collection, the
parameters ``limit`` and ``marker`` can be set in the URI. For example,
``?limit=100&marker=1234)``.

-  The ``marker`` parameter is the ID of the last item in the previous list.
   Items are sorted by update time; when an update time is not available, they
   are sorted by ID.

-  The ``limit`` parameter sets the page size. For example, ``limit=1`` returns
   one item  on the first page. Subsequent `next` and `previous`   links honor
   the initial page size so that a client can follow links to traverse a
   paginated collection without having to input the ``marker`` parameter.


Both the ``limit`` and ``marker`` parameters are optional. If the client
requests a ``limit`` beyond that which is supported by the deployment, the API
service returns an ``overLimit``  (413) response message. A ``marker`` with an
invalid ID will return an ``itemNotFound`` (404)  response.

..  note::
    Paginated collections never return ``itemNotFound`` (404) faults when
    the collection is empty; clients should be prepared to handle an empty
    collection.

Paginated collections contain `next` and `previous` Atom links. The
first page in the list does not contain a previous link; similarly,
the last page in the list does not contain a next link.

In the following examples, a paginated collection of tenants is returned
as three linked pages.

-  The :ref:`first page <auth-paginated-collection-json-one-example>`
   is retrieved via a **GET** to
   ``http://identity.api.openstack.org/v2.0/1234/tenants?limit=1``.

-  The :ref:`second page <auth-paginated-tenant-collection-json-two-example>` is
   retrieved by following the "next" link from the first page.

-  The :ref:`third page <auth-paginated-tenant-collection-json-three-example>` is
   retrieved by following the "next" link from the second page.


.. _auth-paginated-collection-json-one-example:

**Example 3.22. Tenant collection, first page: JSON**

   .. code::

       {
         "tenants": {
           "values": [
             {
               "id": "1234",
               "name": "ACME corp",
               "description": "A description ...",
               "enabled": true
             }
           ],
           "links": [
             {
               "rel": "next",
               "href": "http://identity.api.openstack.org/v2.0/tenants?limit=1&marker=1234"
             }
           ]
         }
      }


.. _auth-paginated-tenant-collection-xml-one-example:

**Example 3.21. Tenant collection, first page: XML**

.. code::

       <?xml version="1.0" encoding="UTF-8"?>
       <tenants xmlns="http://docs.openstack.org/identity/api/v2.0"
                xmlns:atom="http://www.w3.org/2005/Atom">
           <tenant enabled="true" id="1234" name="ACME Corp">
               <description>A description...</description>
           </tenant>
           <atom:link
               rel="next"
               href="http://identity.api.openstack.org/v2.0/tenants?limit=1&amp;marker=1234"/>
       </tenants>


.. _auth-paginated-tenant-collection-json-two-example:

**Example 3.24. Tenant collection, second page: JSON**

.. code::

    {
      "tenants": {
        "values": [
          {
            "id": "3645",
            "name": "Iron Works",
            "description": "A description ...",
            "enabled": true
          }
        ],
        "links": [
          {
            "rel": "next",
            "href": "http://identity.api.openstack.org/v2.0/tenants?limit=1&marker=3645"
          }, {
            "rel": "previous",
            "href": "http://identity.api.openstack.org/v2.0/tenants?limit=1"
          }
        ]
      }
    }

.. _auth-paginated-tenant-collection-xml-two-example:

**Example 3.23. Tenant collection, second page: XML**

.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <tenants xmlns="http://docs.openstack.org/identity/api/v2.0"
             xmlns:atom="http://www.w3.org/2005/Atom">
        <tenant enabled="true" id="3645" name="Iron Works">
            <description>A description...</description>
        </tenant>
        <atom:link
            rel="previous"
            href="http://identity.api.openstack.org/v2.0/tenants?limit=1"/>
        <atom:link
            rel="next"
            href="http://identity.api.openstack.org/v2.0/tenants?limit=1&amp;marker=3645"/>
    </tenants>


.. _auth-paginated-tenant-collection-json-three-example:

**Example 3.26. Tenant collection, page three (last page): JSON**

.. code::

    {
      "tenants": {
        "values": [
          {
            "id": "9999",
            "name": "Bigz",
            "description": "A description ...",
            "enabled": true
          }
        ],
        "links": [
          {
            "rel": "previous",
            "href": "http://identity.api.openstack.org/v2.0/tenants?limit=1&marker=1234"
          }
        ]
      }
    }


.. _auth-paginated-tenant-collection-xml-three-example:

**Example 3.25. Tenant collection, page three (last page): XML**

.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <tenants xmlns="http://docs.openstack.org/identity/api/v2.0"
             xmlns:atom="http://www.w3.org/2005/Atom">
        <tenant enabled="true" id="9999" name="Bigz">
            <description>A description...</description>
        </tenant>
        <atom:link
            rel="previous"
            href="http://identity.api.openstack.org/v2.0/tenants?limit=1&amp;marker=1234"/>
    </tenants>

In the JSON representation, paginated collections contain a values property that contains
the items in the collections. Links are accessed via the links property. This approach
allows for extensibility of both the collection members and of the paginated collection
itself. It also allows collections to be embedded in other objects as shown in the
example below. Here, a subset of groups is presented within a user. To continue retrieving
additional groups belonging to a user, a client must follow the "next" link.


.. _auth-paginated-user-collection-json-example:

**Example 3.28. Paginated roles in a user listing: JSON**

.. code::

    {
      "user": {
        "roles": {
          "values": [
            {
              "tenantId": "1234",
              "id": "Admin"
            }, {
              "tenantId": "1234",
              "id": "DBUser"
            }
          ],
          "links": [
            {
              "rel": "next",
              "href": "http://identity.api.openstack.org/v2.0/tenants/1234/users/u1000/roles?marker=Super"
            }
          ]
        },
        "id": "u1000",
        "username": "jqsmith",
        "email": "john.smith@example.org",
        "enabled": true
      }
    }

.. _auth-paginated-user-collection-xml-example:

**Example 3.27. Paginated roles in a User listing: XML**

.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <user xmlns="http://docs.openstack.org/identity/api/v2.0"
          xmlns:atom="http://www.w3.org/2005/Atom"
          enabled="true" email="john.smith@example.org"
          username="jqsmith" id="u1000">
        <roles>
            <role tenantId="1234" id="Admin"/>
            <role tenantId="1234" id="DBUser"/>
            <atom:link
                rel="next"
                href="http://identity.api.openstack.org/v2.0/tenants/1234/users/u1000/groups?marker=Super"/>
        </roles>
    </user>
