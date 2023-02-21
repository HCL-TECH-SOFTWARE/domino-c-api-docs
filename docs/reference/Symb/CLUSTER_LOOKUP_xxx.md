##### Symbolic Value : Clusters
##### CLUSTER_LOOKUP_xxx - IBM Domino Server Cluster Lookup Flags
---
```
#include <ns.h>
```
**Description :**

These values are used as input to the NSGetServerClusterMates function.  When 
you specify the CLUSTER_LOOKUP_NOCACHE value, the call retrieves the input 
server's cluster member list through a NameLookup on the input server.  The 
client cluster cache is not used for determining this information.  

	When you specify the CLUSTER_LOOKUP_CACHEONLY value, the call is forced 
to retrieve the server's cluster member list from the local client cluster 
cache.  There is no NameLookup performed on the server in this case.

**Sample Usage :**
```
/* Given a server name, get the cluster mates from the cluster cache and from 
the server */

#include <ns.h>

STATUS error;
HANDLE hClusterMateList = NULLHANDLE;

/* get clustermate information only from local client's cluster name cache */
error = NSGetServerClusterMates(ServerName, CLUSTER_LOOKUP_CACHEONLY, 
&hClusterMateList);

if (hClusterMateList != NULLHANDLE)
   OSMemFree(hClusterMateList);

hClusterMateList = NULLHANDLE;

/* get clustermate information only through a NameLookup on the server */
error = NSGetServerClusterMates(ServerName, CLUSTER_LOOKUP_NOCACHE, 
&hClusterMateList);

if (hClusterMateList != NULLHANDLE)
   OSMemFree(hClusterMateList);
```
**See Also :**
[NSGetServerClusterMates](/domino-c-api-docs/reference/Func/NSGetServerClusterMates)
---
