##### Data Type : DSAPI
##### FilterAuthConfigFlags - DSAPI FilterAuthenticate authFlags
---
##### #include <dsapi.h>
**Description :**
The authentication options enabled for the server.  The values for a server can 
be found under the Internet Ports section within the server document.  The 
values can be added together.

kAuthAllowBasic - The server allows basic authentication by providing a user 
name and password.
kAuthAllowAnonymous - The server allows anonymous access to public (non 
protected) documents.
kAuthAllowSSLCert - The server allows SSL authentication using an SSL client 
certificate.
kAuthAllowSSLBasic	- The server allows SSL authentication by providing a 
user name and password.
kAuthAllowSSLAnonymous - The server allows anonymous SSL authentication to 
public (non protected) documents.
kAuthRedirectToSSL - The server allows redirections to SSL authentication for 
documents that are SSL protected.
**See Also :**
[FilterAuthenticate](D:/md_files/FilterAuthenticate.md)
---
