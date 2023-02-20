##### Function : LDAP
##### ldap_sslinit - Initializes a session with an LDAP server.
---
```
#include <ldap.h>
LDAP* ldap_sslinit(

	const  *hostname,
	int  portno,
	int  secure,
	DWORD  ssloptions,
	int  sslprotocolver);
```
**Description :**

This function initializes a secure session with an LDAP server and returns a 
"session handle," a pointer to an opaque structure that MUST be passed to 
subsequent calls pertaining to the session. This routine returns a NULL if the 
session cannot be initialized. Implemented as a macro:
#define ldap_sslinit(hostname, portno, secure, ssloptions, sslprotocolver) \
ND_ldap_sslinit((hostname), (portno), (secure), (ssloptions), (sslprotocolver))

**Parameters :**
Input :
*hostname  -  A space-separated list of hostnames or dotted strings representing the IP address of hosts running an LDAP server to connect to. Each hostname in the list MAY include a port number which is separated from the host itself with a colon (:) character. The hosts will be tried in the order listed, stopping with the first one to which a successful connection is made.

portno  -  The TCP port number to connect to. The default LDAP port of 389 can be obtained by supplying the value zero (0) or the macro LDAP_PORT (389). If a host includes a port number then this parameter is ignored.

secure  -  TRUE to attempt a secure, encrypted connection. FALSE creates an unencrypted connection.

ssloptions  -  Refer  LDAP_SSLOPTS_xxx
/* LDAP_SSLOPTS_SITECERTS - Accept the site certificate even if the Domino server does not have a certificate in common with the LDAP server.  */
/* LDAP_SSLOPTS_ACCEPTEXPCERTS - Allow a connection to the LDAP server, even if the certificate is expired. */
/* LDAP_SSLOPTS_SENDCERTS - Send certificates.  */
/* LDAP_SSLOPTS_SERVERAUTH - Make sure the host name is part of the subject line of the certificate. */
/* LDAP_SSLOPTS_PROMPTXCERT - Prompt for cross certificate.  */

sslprotocolver  -  The SSL protocol version to use.      1 - SSLv2 only
2 - SSLv3 handshake
3 - SSLv3 only
4 - SSLv3 with SSLv2 handshake.
5 - negotiated

Output :
(routine)  -  This routine returns a pointer to a session handle. In case of NULL if the session cannot be initialized.



**Sample Usage :**
```
const char *hostname ="domino-hcl-123.dominodomain.org 10.134.22.5" ; 
int portno=389; int secure =1;
 DWORD ssloptions=0; /*refer LDAP_SSLOPTS_xxx*/
 int sslprotocolver =3; 
if(ld = ldap_sslinit( hostname,portno,secure,ssloptions,sslprotocolver ))
// ldap_sslinit successful
{

printf ( "LDAP sslnit success");
}

```
**See Also :**
---
