.. _how-curl-commands-work:

How cURL commands work
~~~~~~~~~~~~~~~~~~~~~~~

`cURL` is a command-line tool that you can use to interact with
RESTful API interfaces. cURL lets you to transmit and receive
HTTP requests and responses from the command line or a shell
script, which enables you to work with the API directly. It is available
for Linux distributions, Mac OS X, and Windows.

To run the cURL request examples shown in this guide, copy each example
from the HTML version of this guide directly to the command line or a
script.

The following example shows the cURL command syntax for the List users
API operation to retrieve Rackspace Cloud account information by user
name:

 
**Example: cURL Command Example: JSON Request**

.. code::  

    $curl https://identity.api.rackspacecloud.com/v2.0/users/ \
    -X GET \
    -d '{"name":"RackspaceCloudUser"}' \
    -H "Content-type: application/json" \
    -H "X-Auth-Token: $AUTH_TOKEN" --verbose | python -m json.tool

..  note:: 
    The carriage returns in the cURL request examples use a backslash
    (``\``) as an escape character. The escape character allows continuation
    of the command across multiple lines. However, do not include the escape
    character in the JSON or XML request body within the cURL command.

The cURL examples in this guide use the command-line options described in the 
following table.

**Table: cURL Command-Line Options**

+--------------------------------------+--------------------------------------+
| Option                               | Description                          |
+======================================+======================================+
| `-d`                                 | Sends the specified data in a        |
|                                      | **POST** request to the HTTP server. |
|                                      | Use this option to send a JSON or    |
|                                      | XML request body to the server.      |
+--------------------------------------+--------------------------------------+
| `-H`                                 | Specifies an extra HTTP header in    |
|                                      | the request. You can specify any     |
|                                      | number of extra headers. Precede     |
|                                      | each header with the `-H` option.    |
|                                      |                                      |
|                                      | Common headers in Rackspace API      |
|                                      | requests are as follows:             |
|                                      |                                      |
|                                      | -  `Content-Type`. Required for      |
|                                      |    operations with a request body.   |
|                                      |                                      |
|                                      |    Specifies the format of the       |
|                                      |    request body. Following is the    |
|                                      |    syntax for the header where       |
|                                      |    `format` is either `json` or      |
|                                      |    `xml`.                            |
|                                      |                                      |
|                                      |    .. code::                         |
|                                      |                                      |
|                                      |     Content-Type: application/format |
|                                      |                                      |
|                                      |                                      |
|                                      | -  `X-Auth-Token`. Required.         |
|                                      |    Specifies the authentication      |
|                                      |    token.                            |
|                                      |                                      |
|                                      | -  `X-Auth-Project-Id`. Optional.    |
|                                      |    Specifies the project ID, which   |
|                                      |    can be your account number or     |
|                                      |    another value.                    |
|                                      |                                      |
|                                      | -  `Accept`. Optional.               |
|                                      |                                      |
|                                      |    Specifies the format of the       |
|                                      |    response body. Following is the   |
|                                      |    syntax for the header where       |
|                                      |    `format` is either `json` or      |
|                                      |    `xml`. The default is `json`.     |
|                                      |                                      |
|                                      |    .. code::                         |
|                                      |                                      |
|                                      |        Accept: application/format    |
|                                      |                                      |
|                                      |                                      |
+--------------------------------------+--------------------------------------+
| `-i`                                 | Includes the HTTP header in the      |
|                                      | output.                              |
+--------------------------------------+--------------------------------------+
| `-s`                                 | Specifies silent or quiet mode,      |
|                                      | which makes cURL mute. No progress   |
|                                      | or error messages are shown.         |
+--------------------------------------+--------------------------------------+
| `-T`                                 | Transfers the specified local file   |
|                                      | to the remote URL.                   |
+--------------------------------------+--------------------------------------+
| `-X`                                 | Specifies the request method to use  |
|                                      | when communicating with the HTTP     |
|                                      | server. The specified request is     |
|                                      | used instead of the default method,  |
|                                      | which is **GET**.                    |
+--------------------------------------+--------------------------------------+



..  note:: 
    For commands that return a response, you can use the json.tool to pretty-print 
    the output by appending the following code to the command to call the json.tool 

    .. code::  

         | python -m json.tool
    

    To use the json.tool, import the `json module`_. 

    If you run a Python version older than 2.6, import the `simplejson module`_
    and use simplejson.tool.

    You can omit this code if you do not want to pretty-print JSON output.

.. _curl: http://curl.haxx.se/
.. _json module: http://docs.python.org/2/library/json.html
.. _simplejson module: http://simplejson.googlecode.com/svn/tags/simplejson-2.0.9/docs/index.html