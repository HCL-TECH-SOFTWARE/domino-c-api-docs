##### Function : Database
##### NSFDbGetTcpHostName - Get the TCP/IP host and domain name.
---
```
#include <nsfdb.h>
STATUS NSFDbGetTcpHostName(

	DBHANDLE  hdb,
	char *pszHostName,
	WORD  wMaxHostNameLen,
	char *pszDomainName,
	WORD  wMaxDomainNameLen,
	char *pszFullName,
	WORD  wMaxFullNameLen);
```
**Description :**

Get the TCP/IP host and domain name of the server on which a database is 
stored, either a local server or a remote server. Also return the TCP/IP full 
name of the server.

**Parameters :**
Input :
hdb  -  An open DB handle that is used to get the host name and TCP/IP details.

Output :
(routine)  -  Return status from the call either success or an error. The return code include: 
  ERR_NULL_DBHANDLE - on NULL DBHandle. 
  NOERROR - on success.


pszHostName  -  Return TCP/IP host name as a string.

wMaxHostNameLen  -  Return size of host name buffer.

pszDomainName  -  Return TCP/IP domain name as a string.

wMaxDomainNameLen  -  Return size of domain name buffer.

pszFullName  -  Return full TCP/IP name of the host where the opened NSF file is.

wMaxFullNameLen  -  Return size of full name buffer.


**Sample Usage :**
```
/* Get the TCP information we requested. */ 

	#define MAXUSERNAME 256 
	DBHANDLE hdb; 
	char szHostName[MAXPATH] = {0}; 
	char szDomainName[MAXPATH] = {0}; 
	char szFullName[MAXPATH] = {0}; 
	/* Allocate above strings accordingly. */
	if ( Status = NSFDbGetTcpHostName ( 
	 hDB, /* Database Handle. */ 
	 &szHostName, /* Return TCP Host Name. */ 
	 MAXUSERNAME, /* Size of Host Name Buffer. */ 
	 &szDomainName, /* Return TCP Domain Name. */ 
	 MAXUSERNAME, /* Size of Domain Buffer. */ 
	 &szFullName, /* Return Full TCP Name. */ 
	 MAXUSERNAME ) ) /* Size of Full Name Buffer. */ 
	{ 
	 printf("\n NSF DB Get TCP host name failure %e\n", status); 
	  return status; 
	}
```
**See Also :**
---
