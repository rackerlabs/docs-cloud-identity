.. _domain-operations:

Domains
-----------

Use the Domain operations supplied by the :ref:`RAX-AUTH extension <extensions-ovw>` to get
information about the :ref:`domains <domain-concept>` that you can access with the
authentication token supplied in the API request.

A domain establishes an administrative boundary for a customer and a
container for a customer's tenants (accounts) and users.

..  note:: 

	Typically, only Identity service administrators have the capabilities to
	create, update, and delete domains.


**API operations**

.. include:: methods/domains/get-list-domains-v2.0-rax-auth-domains.rst
.. include:: methods/domains/get-get-a-domain-v2.0-rax-auth-domains-domainid.rst


