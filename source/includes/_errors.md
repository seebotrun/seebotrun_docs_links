# Errors

Error codes with a brief explanation are provided below:


Error Code | Meaning
---------- | -------
400 | Bad Request -- The provided request is not valid.
401 | Unauthorized -- The endpoint requested is not valid for the given API key.
403 | Forbidden -- The endpoint requested is not permitted for the given API key.
404 | Not Found -- The specified object could not be found.
405 | Method Not Allowed -- The HTTP verb used for the given endpoint is not supported.
422 | Not Valid -- A validation error has occurred (see response for details).
429 | Too Many Requests -- API limits reached for the given client.
500 | Internal Server Error -- Server error. Please try again later.
503 | Service Unavailable -- Server error. Please try again later.
