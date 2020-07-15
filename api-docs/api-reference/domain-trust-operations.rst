.. _domain-trust-operations:

============
Domain Trust
============

Users can authenticate into a different domain than the one to which they
belong to by creating a domain trust that specifies the roles that can be
assigned to users that use the domain trust. The domain trust is then accepted
by a user that can manage users in the delegate domain.

.. contents::
   :depth: 1
   :local:

.. include:: methods/domain-trusts/post-add-domain-trust.rst
.. include:: methods/domain-trusts/put-update-domain-trust.rst
.. include:: methods/domain-trusts/get-a-domain-trust.rst
.. include:: methods/domain-trusts/get-list-domain-trusts.rst
.. include:: methods/domain-trusts/delete-a-domain-trust.rst
.. include:: methods/domain-trusts/put-update-domain-trust-roles.rst
.. include:: methods/domain-trusts/get-list-domain-trust-roles.rst
.. include:: methods/domain-trusts/post-accept-domain-trust.rst
.. include:: methods/domain-trusts/get-list-domain-trust-user-delegates.rst
.. include:: methods/domain-trusts/get-list-domain-trust-user-group-delegates.rst
.. include:: methods/domain-trusts/get-domain-trust-user-delegate-roles.rst
.. include:: methods/domain-trusts/get-domain-trust-user-group-delegate-roles.rst
.. include:: methods/domain-trusts/put-update-domain-trust-user-group-delegate-roles.rst
.. include:: methods/domain-trusts/put-update-domain-trust-user-delegate-roles.rst
