##### Function : Clusters
##### NSGetServerClusterMates - Returns a list of cluster members, based on input server.
---
```
#include <ns.h>
STATUS LNPUBLIC NSGetServerClusterMates(

	const char far *pServerName,
	DWORD  dwFlags,
	DHANDLE far *phList);
```
**Description :**

The NSGetServerClusterMates function retrieves a handle to a list (of type 
TEXT_LIST) of server names that belong to the same cluster as the server 
specified by pServerName.  If the pServerName parameter is NULL then the 
function retrieves the cluster members of the user's home server.   The dwFlags 
parameter controls how the information is retrieved.  If the 
CLUSTER_LOOKUP_NOCACHE flag is specified then the information is retrieved 
using a NameLookup on the server only.  If the CLUSTER_LOOKUP_CACHEONLY flag is 
specified then the information is retrieved using the client's cluster name 
cache.   If no flags (a value of 0) is specified, then the information is 
retrieved first through the client's cluster name cache and if that is not 
successful, then through a NameLookup on the server.  Note that the list 
returned does not include the input server name (or home server name if NULL 
was specified).   

If successful, the function returns a handle to the text list of cluster 
members in the phList parameter.  The caller should lock the handle down with 
the OSLockObject function before attempting to use the list and unlock it with 
OSUnLockObject when done.  It is also the responsibility of the caller to free 
the memory associated with the handle using the OSMemFree function when 
finished processing the list.  Use the ListGetNumEntries function to determine 
the number of cluster members and the ListGetText to retrieve each entry in the 
text list.

NSGetServerClusterMates uses the Address book specified by the user's location 
record.  Unless  cascading Address books or Directory Assistance is enabled, 
the Notes mail domain field in the user's location record must be set to the 
domain name for the server(s) in the cluster and the Home/mail server field 
must be set to a server in this domain.  If the target server is in a different 
domain than specified in the user's location record then in order for 
NSGetServerClusterMates to succeed, you must have cascading Address books or 
Directory Assistance enabled and the target domain's  Address book must be in 
the list of  Address books to be searched.

**Parameters :**
Input :
pServerName  -  The name of the Lotus Domino Server where the lookup will be performed.  Specify a value of NULL if the client's home server is to be used for the lookup.

dwFlags  -  Lookup Option flags (see CLUSTER_LOOKUP_xxx).

Output :
(routine)  -  If success, NOERROR;
Otherwise, one of a number of possible ERR_xxx errors.


phList  -  Address of location to store text list handle.


**Sample Usage :**
```
/* Given a server name, get the cluster mates without doing any network 
activity */

#include <ns.h>

STATUS error;
DHANDLE hClusterMateList = NULLHANDLE;

error = NSGetServerClusterMates(ServerName, CLUSTER_LOOKUP_CACHEONLY, 
&hClusterMateList);

....

if (hClusterMateList != NULLHANDLE)
	OSMemFree(hClusterMateList);
```
**See Also :**
[CLUSTER_LOOKUP_xxx](/domino-c-api-docs/reference/Symb/CLUSTER_LOOKUP_xxx)
[ListGetNumEntries](/domino-c-api-docs/reference/Func/ListGetNumEntries)
[ListGetText](/domino-c-api-docs/reference/Func/ListGetText)
[OSLockObject](/domino-c-api-docs/reference/Func/OSLockObject)
[OSMemFree](/domino-c-api-docs/reference/Func/OSMemFree)
[OSUnlockObject](/domino-c-api-docs/reference/Func/OSUnlockObject)
---
