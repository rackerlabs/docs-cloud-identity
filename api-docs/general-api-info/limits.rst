======
Limits
======

All accounts, by default, have a preconfigured set of thresholds, or *limits*,
to manage capacity and prevent abuse of the system. The system recognizes two
kinds of limits: *rate limits* and *absolute limits*. Rate limits are
thresholds that are reset after a certain amount of time passes. Absolute
limits are fixed. Rate limits are processed via the `Repose service`_.

Rate limits control the frequency at which the user can issue specific API
requests. Limits can be applied to any of the following entities, depending on
the  data available in the operation request.

- IP address submitting the request.
- user name
- token sent in the ``X-Auth-Token`` header

If a requester exceeds the rate limit, the request is rejected with a 413
``overLimit`` error.  Typically, the request can be resubmitted in a few
seconds.

If the client requests continue to be rejected, check the client, process, or
application  code to verify that API access is managed effectively.  Make sure
that client applications  follow :ref:`best practices
<best-practices-token-management>` for managing  tokens.

The Identity service has its own rate limiting settings, and so does each
node. These settings are managed by the Rackspace operations team. If an
application node is restarted, the last properties set for any of the
Identity service versions are loaded to all nodes.

.. note::

    If the default limits are too low for your particular application,
    contact Rackspace Cloud support to request an increase. All requests
    require reasonable justification.

.. _Repose service: http://www.openrepose.org
