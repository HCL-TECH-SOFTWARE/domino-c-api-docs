##### Data Type : DSAPI
##### FilterResponseHeaders - DSAPI FilterContext / ServerSupport Filter Response Headers
---
##### #include <dsapi.h>
**Description :**
The FilterResponseHeaders structure is used by the ServerSupport callback 
functionality of the FilterContext.  see FilterContext for more information.

responseCode - (Output)  Set to the http status code to send back to the client.
reasonText  - (Output)  Set to the reason response text to add to the response 
line. It can be set to NULL if none is available.
headerText  - (Output)  Points to a buffer of response http headers to append 
to the default response headers if any. Can be set to NULL, if no headers are 
to be appended. If not NULL, each header must be terminated by a carriage 
return and line feed characters ("\r\n"), and the whole sequence of headers 
must end with two "\r\n" sequence.
**See Also :**
[FilterContext](D:/md_files/FilterContext.md)
[ServerSupportTypes](D:/md_files/ServerSupportTypes.md)
---
