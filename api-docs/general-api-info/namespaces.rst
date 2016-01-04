.. _namespaces:

Namespaces
~~~~~~~~~~~~

The API operations described in the :ref:`Identity API Operations 
Reference <api-reference-intro>` are enabled by a combination of the
core Identity API and multiple API extensions. You can read more about
extensions, including how to request details about all or specific
extensions, at :ref:`Extensions <extensions-ovw>`.

Depending upon which operations you perform, you might see evidence of one
or several extensions involved in processing your request. The most
obvious evidence is the inclusion of namespaces in XML responses. You
can identify the extensions involved in processing a request by
examining the namespaces shown in the response.

A namespace is a container within which information has a specific
meaning; in a different container, the meaning might be different.
Specifying a namespace as the source of a definition is widely used as a
way of choosing among multiple available meanings; context and scope are
closely-related ideas.

In the example below, ``xmlns`` associates each namespace label (such as
``ns1``) with a URL (such as
``http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0``). Examining
the list of namespaces shows that the core Identity API makes it
possible to list ``credentials`` and the ``RAX-KSKEY`` extension adds to
that by making it possible to list a specific kind of credentials,
``apiKeyCredentials``.

 
**Example: Multiple Namespaces in an XML Response**

.. code::  

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <ns2:credentials 
        xmlns:ns1="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0" 
        xmlns:ns2="http://docs.openstack.org/identity/api/v2.0" 
        xmlns:ns3="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"           
        xmlns:ns4="http://docs.rackspace.com/identity/api/ext/RAX-KSQA/v1.0" 
        xmlns:ns5="http://docs.openstack.org/common/api/v1.0" 
        xmlns:ns6="http://docs.rackspace.com/identity/api/ext/RAX-KSGRP/v1.0" 
        xmlns:ns7="http://docs.openstack.org/identity/api/ext/OS-KSCATALOG/v1.0" 
        xmlns:ns8="http://www.w3.org/2005/Atom">
        <ns3:apiKeyCredentials 
            username="bobbuilder" 
            apiKey="0f97f489c848438090250d50c7e1eaXZ"/>
    </ns2:credentials>

The core Identity API, defined in ``ns2``, supports ``<credentials>``. This association is 
valid only within this example. You might see namespaces identified differently in 
responses that you generate.

The ``RAX-KSKEY`` extension is defined in ``ns3``. This association is valid only 
within this example. You might see namespaces identified differently in responses that 
you generate. 

Support for ``<apiKeyCredentials>`` is provided by the extension defined as ``ns3``. This 
association is valid only within this example; you might see namespaces identified 
differently in responses that you generate.


If you are programmatically parsing responses that describe multiple
namespaces, do not assume that the prefixes that identify
namespaces are constant. In this example, ``ns2`` identifies the
namespace for the Identity API and ``ns3`` identifies the namespace for
the ``RAX-KSKEY`` extension. Under other circumstances, other prefixes
could be associated with those namespaces.
