Limits
-------------

Rate limits control the frequency at which the user can issue specific API requests.
Limits can be applied to any of the following entities, depending on the 
data available in the operation request.

- IP address submitting the request.
- user name
- token sent in the ``X-Auth-Token`` header

If a requester exceeds the rate limit, the request is rejected with a 413 ``overLimit`` error. 
Typically, the request can be resubmitted in a few seconds. 

If the client requests continue to be rejected, check the client, process, or application 
code to verify that API access is managed effectively.  Make sure that client applications 
follow :ref:`best practices <best-practices-token-management>` for managing 
tokens. 

The Identity service has its own rate limiting settings, and so does each node. If an 
application node is restarted, the last properties set for any of the Identity service 
versions are loaded to all nodes.

Identity service administrators and developers manage the rate limit settings and 
configuration, but Identity administrators can use the Rate limit API operations to get 
information about rate limit configuration and events to troubleshoot problems.
