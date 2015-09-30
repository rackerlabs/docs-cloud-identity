.. _faults:

Faults
~~~~~~~~~

API calls that return an error return one of the following fault objects. All fault 
objects extend from the base fault, ``serviceFault``, for easier exception handling 
for languages that support it.

Rackspace Cloud service APIs return HTTP codes that denote the type of response.

-  Successful response codes are returned only if all configured
   providers were successful in processing the request.

-  Error response codes are accompanied by an ``application/json``
   response body that contains the error messages.
   

The following table lists possible responses with their associated codes
and descriptions. The description included is a general description of the error code. 
The description returned in the response body varies based on the context and features 
of the API operation request. 

+--------------------------+--------------------------+-----------------------+
| Fault Element            | Associated               | Description           |
|                          | error codes              |                       |
+--------------------------+--------------------------+-----------------------+
| serviceFault             | 200                      | The request has       |
|                          |                          | succeeded.            |
|                          |                          | (Some API operations  |
|                          |                          | return 201 instead.)  |
+--------------------------+--------------------------+-----------------------+
| Created                  | 201                      | The request has been  |
|                          |                          | fulfilled and a       |
|                          |                          | resource was created. |
+--------------------------+--------------------------+-----------------------+
| Accepted                 | 202                      | The request has been  |
|                          |                          | accepted for          |
|                          |                          | processing.           |
+--------------------------+--------------------------+-----------------------+
| No Content               | 204                      | The request has been  |
|                          |                          | fulfilled but does not|
|                          |                          | return a              |
|                          |                          | representation (that  |
|                          |                          | is, the response is   |
|                          |                          | empty).               |
+--------------------------+--------------------------+-----------------------+
| Bad Request              | 400                      | The request was not   |
|                          |                          | understood or was     |
|                          |                          | missing required      |
|                          |                          | parameters.           |
+--------------------------+--------------------------+-----------------------+
| Unauthorized             | 401                      | Authentication failed,|
|                          |                          | or the user does not  |
|                          |                          | have permissions for a|
|                          |                          | requested operation.  |
+--------------------------+--------------------------+-----------------------+
| Forbidden                | 403                      | The server understood |
|                          |                          | the request but       |
|                          |                          | refused to fulfill it.|
+--------------------------+--------------------------+-----------------------+
| Not Found                | 404                      | A requested resource  |
|                          |                          | was not found.        |
+--------------------------+--------------------------+-----------------------+
| Method Not Allowed       | 405                      | The request method is |
|                          |                          | not supported for this|
|                          |                          | resource.             |
+--------------------------+--------------------------+-----------------------+
| Request Entity Too Large | 413                      | The server is refusing|
|                          |                          | to process a request  |
|                          |                          | because the request   |
|                          |                          | entity is larger than |
|                          |                          | the server is willing |
|                          |                          | or able to process.   |
+--------------------------+--------------------------+-----------------------+
| Internal Server Error    | 500                      | The service           |
|                          |                          | encountered an        |
|                          |                          | unexpected condition  |
|                          |                          | that prevented it     |
|                          |                          | from fulfilling the   |
|                          |                          | request.              |
+--------------------------+--------------------------+-----------------------+
| Service Unavailable      | 503                      | The service is        |
|                          |                          | temporarily           |
|                          |                          | unavailable, for      |
|                          |                          | example, for scheduled|
|                          |                          | platform maintenance. |
|                          |                          | Try again later.      |
+--------------------------+--------------------------+-----------------------+

 
**Example 4.3. Error message example**

.. code::  

    HTTP/1.1 400 Bad Request
    Content-Type: application/json

    {
      "title": "Unsupported limit",
      "description": "The given limit cannot be negative, and cannot be greater than 50.",
      "code": 1092,
      "link": {
        "rel": "help",
        "href": "http://docs.example.com/messages#limit",
        "text": "API documentation for the limit parameter"
      }
    }


The following example shows the ``itemNotFound`` error.


**Example 3.44. Item Not Found Fault: JSON**

.. code::  

    {
      "itemNotFound": {
        "message": "Item not found.",
        "details": "Error Details...",
        "code": 404
      }
    }




                
