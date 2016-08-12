.. _authentication-info-intro:

=================================
Authentication and access control
=================================

You can use the Identity service to authenticate and get an
authentication token, user account information, and
a service catalog that lists the services that you can access with the
authentication token supplied in the response. To learn more about
authentication, see
:ref:`Annotated authenticate request and response <annotated-auth-req-resp>`.

You can protect your Rackspace Cloud account from unauthorized use by
setting up and using multi-factor authentication. To learn more, see
:ref:`Multi-factor authentication <multifactor-authenication-ovw>`.

Rackspace Cloud services use role-based access control to determine which
operations an authenticated user can perform. User accounts have an Identity
role that determines permissions for the Identity service and service-specific
roles that determine permissions for other Rackspace Cloud services.  To learn
more about these roles, see  :ref:`Identity roles and users
<roles-and-role-assignments>`.

.. toctree:: :hidden:
   :maxdepth: 2

   sample-auth-req-response
   identity-roles-users
   Role-based access control <role-based-access-control>
