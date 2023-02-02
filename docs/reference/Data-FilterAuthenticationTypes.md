##### Data Type : DSAPI
##### FilterAuthenticationTypes - DSAPI FilterAuthenticate authType
---
##### #include <dsapi.h>
**Description :**
The type of authorization.  If the filter handles this event, the filter must 
set authType within the FilterAuthenticate structure to one of these values.

kNotAuthentic - User's credentials failed authentication. The http stack must 
terminate the processing of the request. 
kAuthenticBasic - User's name and password has passed authentication. The 
authentication phase should be terminated, and the next phase in the processing 
of the request started.
kAuthenticClientCert - The SSL authentication using an SSL client certificate 
has succeeded. The authentication phase should be terminated, and the next 
phase in the processing of the request started.
**See Also :**
[FilterAuthenticate](D:/md_files/FilterAuthenticate.md)
---
