.. _domain-operations:

=======
Domains
=======

A domain establishes an administrative boundary for a customer and a
container for customer tenants (accounts) and users.

Use the following Domain operations supplied by the :ref:`RAX-AUTH extension
<extensions-ovw>` to get information about available
:ref:`domains <domain-concept>` or about the domain associated with a
specified user account.

.. contents::
   :depth: 1
   :local:

.. include:: methods/domains/get-list-domains-v2.0-rax-auth-domains.rst
.. include:: methods/domains/get-get-a-domain-v2.0-rax-auth-domains-domainid.rst
.. include:: methods/domains/put-update-a-domain.rst

..  note::

     Typically, only Identity service administrators have the capabilities to
     create, update, and delete domains.
