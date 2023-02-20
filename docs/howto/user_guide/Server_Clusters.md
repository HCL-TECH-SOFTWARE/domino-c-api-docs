##### Chapter 13-2
##### Server Clusters

<b><font size="5" color="#000080">Introduction</font></b><br>
<br>
A cluster is a group of up to six Domino servers interconnected  to form a team that cooperates to provide services or resources to clients. Some advantages of clusters are high data availability, tightly synchronized databases, and scalability. Clusters provide failover protection for business-critical databases and servers, including passthru server failover to other servers in the cluster. With failover, users can still access a database when a server goes down.  A workload balancing feature further ensures that heavily-used servers can pass requests to other cluster servers and that work is evenly distributed for optimized performance. <br>
<br>
Typically, each cluster contains multiple database replicas that are kept tightly synchronized in the cluster by the Cluster Replicator. There are six other cluster components, such as the Cluster Database Directory Manager server task (CLDBDIR), that manage and monitor servers and databases in a cluster. For details about these components, see the <i>Domino Administration Help </i>documentation.<br>
<br>
The HCL C API for Domino and Notes provides functions that you can use to programmatically access a server cluster. Any administrative application that lets you view or control a clustered environment can use these functions. The following table describes the types of information available when you use the HCL C API for Domino and Notes:<br>
<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="29%"><b><i><font size="2">Information type</font></i></b></td><td width="37%"><b><i><font size="2">Description</font></i></b></td><td width="34%"><b><i><font size="2">API Routine</font></i></b></td></tr>

<tr valign="top"><td width="29%"><b><font size="2">Server cluster name</font></b></td><td width="37%"><font size="2">Name of the cluster to which a Domino server belongs</font></td><td width="34%"><font size="2">NSPingServer</font></td></tr>

<tr valign="top"><td width="29%"><b><font size="2">Server availability</font></b></td><td width="37%"><font size="2">Determines whether a server is reachable and, if so, retrieves the server availability index (optional). The index value (0-100) defines the current workload of the server. When the server availability value is less than the configured availability threshold value (as specified in the notes.ini Server_Availability_Threshold setting), the server enters a BUSY state.</font></td><td width="34%"><font size="2">NSPingServer</font></td></tr>

<tr valign="top"><td width="29%"><b><font size="2">Server cluster members </font></b></td><td width="37%"><font size="2">Names of servers that belong to a specific cluster </font></td><td width="34%"><font size="2">NSPingServer</font><br>
<font size="2">NSGetServerClusterMates</font></td></tr>

<tr valign="top"><td width="29%"><b><font size="2">Database availability attributes</font></b></td><td width="37%"><font size="2">Database attributes that indicate availability status. You can programmatically modify a database to be available (marked in service), unavailable (marked out of service), or ready for permanent deletion (marked for delete).</font></td><td width="34%"><font size="2">NSFDbMarkForDelete</font><br>
<font size="2">NSFDBMarkInService</font><br>
<font size="2">NSFDBMarkOutOfService</font><br>
<font size="2">NSFDbGetOptions</font></td></tr>

<tr valign="top"><td width="29%"><b><font size="2">Clustered database failover</font></b></td><td width="37%"><font size="2">Provides support for database open failover.</font></td><td width="34%"><font size="2">NSFDbOpenExtended </font></td></tr>
</table>

<ul>
<ul></ul>
</ul>
The remainder of this chapter describes how you use the HCL C API for Domino and Notes toolkit to obtain cluster information and services. It includes code segments from the CLUMON sample program.<br>
<br>
<br>
<b><font size="5" color="#000080">Server Cluster Name</font></b><br>
<br>
The C API routine NSPingServer allows a remote application to retrieve the name of the cluster to which a server belongs. In addition to determining if a specified Domino server is reachable, this function optionally retrieves the specified server's availability index and a list (of type TEXT_LIST) of all members in the server cluster. If the server is in a BUSY state (that is, the server is too busy to accept incoming requests), the return status is set to ERR_SERVER_UNAVAILABLE. If the system administrator has restricted the server, the return status is set to ERR_SERVER_RESTRICTED. In either state, the server continues to return its availability index and list of cluster members if the pdwIndex and phList parameters are not NULL. The function does not return the cluster information if the server is unreachable or not running. For more information about NSPingServer, see the <i>Reference</i><i>.</i><br>
<br>
The CLUMON sample code below uses NSPingServer in the following algorithm to get the cluster name for a specified server name:<br>
   
<ol type="1">
<li>Call NSPingServer to retrieve the TEXT_LIST handle, of which the first item is the server cluster name. The pdwIndex parameter is set to NULL because the availability index value is not desired.
<li>Use OSLock /OSLockObject to lock down the text list.
<li>Use ListGetNumEntries to validate the number of entries and ListGetText to get the cluster name (first item).
<li>Use OSUnlock/OSUnlockObject to unlock the text list.</ol>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>Server Cluster Name Retrieval Routine for Sample Program CLUMON (clfunc.c)</b></td></tr>
</table>
<tt><font size="2">STATUS GetServerCluster ( char FAR *pServerName, &nbsp;/* server name */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;char FAR *pClusterName &nbsp;/* returned cluster name */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;)<br>
{<br>
 &nbsp; &nbsp;WORD &nbsp; &nbsp; &nbsp; &nbsp;wNumListEntries = 0;<br>
 &nbsp; &nbsp;WORD &nbsp; &nbsp; &nbsp; &nbsp;wBufferLen = 0;<br>
 &nbsp; &nbsp;void FAR &nbsp; &nbsp;*lpList;<br>
 &nbsp; &nbsp;char &nbsp; &nbsp; &nbsp; &nbsp;*pBuffer;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; char	 &nbsp; &nbsp;achClusterName[MAXUSERNAME];<br>
 &nbsp; &nbsp;HANDLE &nbsp; &nbsp; &nbsp;hList=NULLHANDLE;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; char &nbsp; &nbsp;szCanonServerName[MAXUSERNAME]; /* Canonicalized Name of Server */<br>
 &nbsp; &nbsp;STATUS &nbsp;nError;<br>
 &nbsp; &nbsp;<br>
 &nbsp; &nbsp;/* Canonicalize the servername if it isn't already done. &nbsp;<br>
 &nbsp; &nbsp; * The NSPingServer should use a canonicalized servername as input<br>
 &nbsp; &nbsp; */<br>
 &nbsp; &nbsp;nError = DNCanonicalize( 0L, NULL, pServerName, (char FAR*)szCanonServerName, <br>
						MAXUSERNAME, NULL);<br>
 &nbsp; &nbsp;if (nError != NOERROR)<br>
 &nbsp; &nbsp; &nbsp; &nbsp;return (nError);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* and call NSPingServer - only interested in cluster list */<br>
 &nbsp; &nbsp;nError = NSPingServer( (char FAR *)szCanonServerName, NULL, &amp;hList);<br>
 &nbsp; &nbsp;<br>
 &nbsp; &nbsp;/* If the server is unavailable, proceed - can still get its cluster name */<br>
 &nbsp; &nbsp;if (!nError || (ERR(nError) == ERR_SERVER_UNAVAILABLE))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;/* if the list handle is NULL, that indicates that this server doesn't<br>
 &nbsp; &nbsp; &nbsp; &nbsp; * belong to a cluster<br>
 &nbsp; &nbsp; &nbsp; &nbsp; */<br>
 &nbsp; &nbsp; &nbsp; &nbsp;if (hList == NULLHANDLE)<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;return(nError = NPNERR_NOT_CLUSTER_MEMBER);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;else<br>
 &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Lock down the list so we can use it */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;lpList = OSLock( void, hList);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;wNumListEntries = ListGetNumEntries( lpList, FALSE);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;if (wNumListEntries &gt; 0)<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* The first entry in the list is the cluster name */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;nError = ListGetText( lpList, FALSE, 0, &amp;pBuffer, &amp;wBufferLen);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;if (!nError)<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;strncpy( achClusterName, pBuffer, wBufferLen);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;achClusterName[wBufferLen] = '\0';</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; OSUnlock( hList);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;lstrcpy( pClusterName, (char FAR *)achClusterName); &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;}<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;else<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;nError = NPNERR_GETTING_CLUSTER_NAME;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;OSUnlock( hList);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;goto Cleanup;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;}<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;}<br>
	 &nbsp;} &nbsp; &nbsp;<br>
 &nbsp; &nbsp;}<br>
 &nbsp; &nbsp;else<br>
 &nbsp; &nbsp; &nbsp; &nbsp;return(nError);</font></tt><br>
<br>
<tt><font size="2">Cleanup:<br>
 &nbsp; &nbsp;if (hList != NULLHANDLE) &nbsp; &nbsp; &nbsp; &nbsp;<br>
	 &nbsp;OSMemFree( hList);<br>
		<br>
 &nbsp; &nbsp;return( nError);<br>
}</font></tt><br>
<br>
NOTE: The NPNERR_xxx symbols are defined in the sample header file clumon.h and are not returned error codes that the HCL C API for Domino and Notes can process.<br>
<br>
<br>
<b><font size="5" color="#000080">Server Availability</font></b><br>
<br>
You can also use NSPingServer to retrieve the availability index of a clustered server. For a description of NSPingServer, refer to the <i>Reference</i><i>.</i><br>
<br>
The following code illustrates how the CLUMON sample uses NSPingServer to get the server availability index for a specified server name. The routine calls NSPingServer to retrieve and return the availability (load) index value. The phList parameter is set to NULL because the TEXT_LIST handle is not desired.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>Server Cluster Availability Retrieval Routine for Sample Program CLUMON (clfunc.c)</b></td></tr>
</table>
<tt><font size="2">STATUS GetServerLoad ( char FAR *pServerName, /* server name */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; DWORD FAR *dwLoadIndex /* returned availability */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; )<br>
{<br>
 &nbsp; &nbsp;char &nbsp; &nbsp;szCanonServerName[MAXUSERNAME]; /* Canonicalized Name of Server */<br>
 &nbsp; &nbsp;STATUS &nbsp;nError;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* Canonicalize the servername if it isn't already done. &nbsp;<br>
 &nbsp; &nbsp; * The NSPingServer should use a canonicalized servername as input<br>
 &nbsp; &nbsp; */<br>
 &nbsp; &nbsp;nError = DNCanonicalize( 0L, NULL, pServerName, (char FAR*)szCanonServerName, <br>
 &nbsp; &nbsp; 	 &nbsp; &nbsp;						MAXUSERNAME, NULL);<br>
 &nbsp; &nbsp;if (nError != NOERROR)<br>
 &nbsp; &nbsp; &nbsp; &nbsp;return (nError);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* Call NSPingServer - only interested in load index */<br>
 &nbsp; &nbsp;nError = NSPingServer( (char FAR *)szCanonServerName, dwLoadIndex, NULL);<br>
 &nbsp; &nbsp;<br>
 &nbsp; &nbsp;/* And return the status */<br>
 &nbsp; &nbsp;return( nError);<br>
}</font></tt><br>
<br>
<br>
<b><font size="5" color="#000080">Server Cluster Members</font></b><br>
<br>
The text list parameter returned by NSPingServer contains the names of all servers that are members of the cluster, including the specified input server. Optionally, the API function NSGetServerClusterMates provides a dedicated, flexible method of retrieving the server cluster members from a remote application.  <br>
<br>
NSGetServerClusterMates retrieves a handle to a list (of type TEXT_LIST) of server names that belong to the same cluster as the server specified by pServerName. If the pServerName parameter is NULL, the function retrieves the cluster members of the user's home server. The dwFlags parameter controls how the information is retrieved. If you specify the CLUSTER_LOOKUP_NOCACHE flag, the information is retrieved using a NameLookup on the server only. If you specify the CLUSTER_LOOKUP_CACHEONLY flag, the information is only retrieved through the client's cluster name cache.<br>
<br>
Both NSPingServer and NSGetServerClusterMates have special  advantages. If your application requires that a particular Domino server always be running and that it report all cluster information, use  NSPingServer, since it returns the information in a single call. If your application is more administrative and needs to dynamically locate servers in a cluster, NSGetServerClusterMates is a better choice due to its local caching capabilities.  For descriptions of NSPingServer and NSGetServerClusterMates, refer to the <i> Reference</i><i>.</i><br>
<br>
The following code illustrates how the CLUMON sample uses NSGetServerClusterMates to get cluster information for a specified server name. The method calls NSGetServerClusterMates with the passed lookup flag parameter to retrieve the TEXT_LIST handle of the server's cluster members.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>Server Cluster Members Retrieval Routine for Sample Program CLUMON (clfunc.c)</b></td></tr>
</table>
<tt><font size="2">STATUS GetServerClusterMates ( char FAR *pServerName, /* server name */ <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; DWORD dwLookupFlags, &nbsp; /* lookup flags */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; HANDLE *hRetList &nbsp; &nbsp; &nbsp; /* returned clustermates */ &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; )<br>
{<br>
 &nbsp; &nbsp;char &nbsp; &nbsp;szCanonServerName[MAXUSERNAME]; /* Canonicalized Name of Server */<br>
 &nbsp; &nbsp;STATUS &nbsp;nError;<br>
 &nbsp; &nbsp;<br>
 &nbsp; &nbsp;/* Canonicalize the servername if it isn't already done. &nbsp;<br>
 &nbsp; &nbsp; * The NSGetServerClusterMates requires a fully canonicalized servername<br>
 &nbsp; &nbsp; * as input.<br>
 &nbsp; &nbsp; */<br>
 &nbsp; &nbsp;nError = DNCanonicalize( 0L, NULL, pServerName, (char FAR*)szCanonServerName, <br>
 &nbsp; &nbsp; &nbsp; &nbsp;						MAXUSERNAME, NULL);<br>
 &nbsp; &nbsp;if (nError != NOERROR)<br>
 &nbsp; &nbsp; &nbsp; &nbsp;return (nError);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* And call NSGetServerClusterMates */<br>
 &nbsp; &nbsp;nError = NSGetServerClusterMates( (char FAR *)szCanonServerName, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;dwLookupFlags, hRetList);<br>
 &nbsp; &nbsp;<br>
 &nbsp; &nbsp;/* cleanup if error */	 &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp;if (nError != NOERROR)<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;if (*hRetList != NULLHANDLE) &nbsp; &nbsp; &nbsp; &nbsp;<br>
	 &nbsp;{<br>
		OSMemFree( *hRetList);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;	*hRetList = NULLHANDLE;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;}<br>
 &nbsp; &nbsp;}<br>
 &nbsp; &nbsp;return( nError);<br>
}</font></tt><br>
<br>
NOTE: If there is a successful return, the calling routine is responsible for freeing the allocated text list handle returned by NSGetServerClusterMates. As with the text list returned by NSPingServer, the calling routine should use the OS Memory routines to lock and unlock the text list handle and the Text List Manipulation routines to retrieve the list count and each list item.<br>
<br>
<br>
<b><font size="5" color="#000080">Database Availability Attributes</font></b><br>
<br>
The Domino server cluster environment allows you to manage database access without restricting server level access.  You do this by modifying the database option flags to mark whether the file is in service for user open access.   <br>
<br>
Domino provides three database attributes that let you specify whether a database is available for user access:<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="33%"><font size="2">Attribute</font></td><td width="33%"><font size="2">Description</font></td><td width="33%"><font size="2">API Routine</font></td></tr>

<tr valign="top"><td width="33%"><font size="2">Out of service</font></td><td width="33%"><font size="2">Users cannot open the database. New open database requests fail over to a replica if possible.</font></td><td width="33%"><font size="2">NSFDbMarkOutOfService</font></td></tr>

<tr valign="top"><td width="33%"><font size="2">In service</font></td><td width="33%"><font size="2">Use this attribute if you have marked a database out of service and now want to restore user access to the database. </font></td><td width="33%"><font size="2">NSFDbMarkInService</font></td></tr>

<tr valign="top"><td width="33%"><font size="2">Pending delete</font></td><td width="33%"><font size="2">After all users terminate their connection to the database, Domino pushes any changes to another replica and deletes the database. </font></td><td width="33%"><font size="2">NSFDbMarkForDelete</font></td></tr>
</table>
<br>
If a database is marked in service, a database open request is permitted. If a database is marked out of service, open requests are restricted until the database is marked in service again. This way, an administrative task can be performed against an out of service database without restricting access to other databases on the server. The Cluster Database Directory Manager (CLDBDIR) server task manages the databases on the clustered server to enforce the appropriate restrictions based on the current database option marks.<br>
<br>
The HCL C API for Domino and Notes provides the following three functions that allow administrative users (with Designer access) to mark a database that the CLDBDIR server task will manage. You can call these functions only against databases that reside on clustered servers.   <br>
<br>
NSFDbMarkInService - Marks a database file in service. The CLDBDIR task removes any database open access restrictions from a database file that is marked in service.
<p>NSFDbMarkOutOfService - Marks a database file out of service. The CLDBDIR task restricts open access to a database file that is marked out of service. 
<p>NSFDbMarkForDelete - Marks a database file for pending deletion. The CLDBDIR task restricts access to a database file that is marked for deletion (the database is also automatically marked out of service) and permanently deletes the file after all active database sessions terminate. Marking a database file for deletion is irreversible, since you cannot programmatically mark a database file back in service. You must have Manager access to the database file to mark it for deletion.   
<p><br>
The following database option flags support these functions:<br>
<br>
DBOPTION_OUT_OF_SERVICE - Set by a successful NSFDbMarkOutOfService and a successful NSFDbMarkForDelete. Unset by a successful NSFDbMarkInService.
<p>DBOPTION_MARKED_FOR_DELETE -Set by a successful NSFDbMarkForDelete.
<p><br>
NSFDbGetOptions retrieves database option flags. Since you must supply an open database handle when calling NSFDbGetOptions, the function returns a database access error for databases with the DBOPTION_OUT_OF_SERVICE option flag set.  <br>
<br>
For more information about NSFDbMarkInService, NSFDbMarkOutOfService, NSFDbMarkForDelete, and NSFDbGetOptions, and for DBOPTION_xxx symbol definitions, refer to the <i>Reference.</i><br>
<br>
The following code illustrates how the CLUMON sample calls NSFDbMarkInService, NSFDbMarkOutOfService, and NSFDbMarkForDelete. The routine makes the appropriate function call based on the checkbox control input set from the sample dialog box interface. <br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>Routine to Mark Clustered Databases for Sample Program CLUMON (clfunc.c)</b></td></tr>
</table>
<tt><font size="2">STATUS SetDBMarks ( char FAR *pServerName, /* database server name */ <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;char FAR *pDBName, &nbsp; &nbsp; /* database file name */ <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;WORD wMarkFlag &nbsp; &nbsp; &nbsp; &nbsp; /* mark flag */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;)<br>
{<br>
 &nbsp; &nbsp;STATUS &nbsp;nError;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; char &nbsp; &nbsp;szCanonServerName[MAXUSERNAME]; &nbsp;/* Canonicalized Name of Server */<br>
 &nbsp; &nbsp;char &nbsp; &nbsp;szNetPathName[MAXPATH]; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Network Path of Database */</font></tt><br>
<br>
<tt><font size="2">	/* Canonicalize the Servername */<br>
 &nbsp; &nbsp;nError = DNCanonicalize( 0L, NULL, pServerName, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;(char FAR *)szCanonServerName, MAXUSERNAME, NULL);<br>
 &nbsp; &nbsp;if (nError != NOERROR)<br>
 &nbsp; &nbsp; &nbsp; &nbsp;return nError;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* Construct NetPath */<br>
 &nbsp; &nbsp;nError = OSPathNetConstruct (NULL, (char FAR *)szCanonServerName, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;pDBName, (char FAR *)szNetPathName);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* And call relevant NFSMark functions */<br>
 &nbsp; &nbsp;/* NSFDbMarkInService() */<br>
 &nbsp; &nbsp;if ( wMarkFlag &amp; MARK_IN_SERVICE )<br>
 &nbsp; &nbsp; &nbsp; &nbsp;nError = NSFDbMarkInService ( (char FAR *)szNetPathName );<br>
 &nbsp; &nbsp;if (nError != NOERROR )<br>
 &nbsp; &nbsp; &nbsp; &nbsp;return nError;<br>
 &nbsp; <br>
 &nbsp; &nbsp;/* NSFDbMarkOutOfService() */<br>
 &nbsp; &nbsp;if ( wMarkFlag &amp; MARK_OUT_SERVICE )<br>
 &nbsp; &nbsp; &nbsp; &nbsp;nError = NSFDbMarkOutOfService ( (char FAR *)szNetPathName );<br>
 &nbsp; &nbsp;if (nError != NOERROR )<br>
 &nbsp; &nbsp; &nbsp; &nbsp;return nError;<br>
 &nbsp; <br>
 &nbsp; &nbsp;/* NSFDbMarkForDelete() */<br>
 &nbsp; &nbsp;if ( wMarkFlag &amp; MARK_DELETE )<br>
 &nbsp; &nbsp; &nbsp; &nbsp;nError = NSFDbMarkForDelete ( (char FAR *)szNetPathName );</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; return nError;<br>
}</font></tt><br>
<br>
NOTE: This routine is called by the Windows message handler routine for the particular dialog box. The calling routine contains the logic that prevents users from having the &quot;in service&quot; checkbox checked at the same time as the &quot;out of service&quot; or &quot;for delete&quot; checkboxes. Also note that the MARK_xxx flags are defined in the sample header file clumon.h.
<ul></ul>
<br>
<b><font size="5" color="#000080">Clustered Database Failover</font></b><br>
<br>
Failover is a cluster's ability to redirect requests from one server to another. When a user tries to access a database on a server that is unavailable or in heavy use, Domino can connect the user to a replica of the database on  another server in the cluster.  For information about user activities that can trigger failover, refer to the <i>Domino Administration Help </i>documentation.<br>
<br>
To programmatically leverage the fault resiliency and workload balancing feature of a Domino server cluster, database open failover is supported if you call the API function NSFDbOpenExtended with the  DBOPEN_CLUSTER_FAILOVER  Options flag set. If one of the above failover conditions is present, the database open request  automatically fails over to another server that is a member of the same cluster. This failover process is transparent to the caller. If the database open fails over and the caller wishes to determine the server/database that is actually opened, use the API function NSFDbPathGet function. To determine if failover occurs, the caller can then compare the PathName string specified in NSFDbOpenExtended with the retCanonicalPathName string returned by NSFDbPathGet.   <br>
<br>
For details about NSFDbOpenExtended and NSFDbPathGet, refer to the <i>Reference</i><i>.</i><br>
<br>
Note that the same clustered database failover behavior described for NSFDbOpenExtended with the DBOPEN_CLUSTER_FAILOVER Option flag also occurs when a user opens the targeted database from a Notes client (Release 4.5 and later).<br>
<br>
The following code illustrates how the CLUMON sample opens a database with failover support, determines whether database open failover has occurred and to which clustered server, and uses the database handle to retrieve the mark option flags.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>Routine to Support Database Open Failover Sample Program CLUMON (CLFUNC.C)</b></td></tr>
</table>
<tt><font size="2">STATUS GetDBMarks ( char FAR *pServerName, &nbsp;/* database server name */ <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;char FAR *pDBName, &nbsp; &nbsp; &nbsp;/* database file name */ <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;DWORD &nbsp; &nbsp;*dwOptionMask, /* open option flags */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;BOOL &nbsp; &nbsp; *bFailover &nbsp; &nbsp; /* TRUE if server failover */ &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;)<br>
{<br>
 &nbsp; &nbsp;STATUS &nbsp; &nbsp; &nbsp;nError;<br>
 &nbsp; &nbsp;HANDLE &nbsp; &nbsp; &nbsp;hDb; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* NSFDbOpenExtended parameters */<br>
 &nbsp; &nbsp;TIMEDATE &nbsp; &nbsp;dataNoteMod;<br>
 &nbsp; &nbsp;TIMEDATE &nbsp; &nbsp;nonDataNoteMod;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; char &nbsp; &nbsp;szCanonServerName[MAXUSERNAME]; /* Canonicalized Name of Server */<br>
 &nbsp; &nbsp;char &nbsp; &nbsp;szNetPathName[MAXPATH]; &nbsp; &nbsp; &nbsp; &nbsp; /* Network Path of Database */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; char &nbsp; &nbsp;szFailoverServerName[MAXUSERNAME]; /* Failover Server Name */<br>
 &nbsp; &nbsp;char &nbsp; &nbsp;szFailoverDBName[MAXUSERNAME]; &nbsp; &nbsp; /* Failover DB Name */<br>
 &nbsp; &nbsp;char &nbsp; &nbsp;szFailoverPathName[MAXPATH]; &nbsp; &nbsp; &nbsp; /* Expanded Failover Path Name */ </font></tt><br>
<br>
<tt><font size="2">	/* Canonicalize the Servername */<br>
 &nbsp; &nbsp;nError = DNCanonicalize( 0L, NULL, pServerName, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;(char FAR *)szCanonServerName, MAXUSERNAME, NULL);<br>
 &nbsp; &nbsp;if (nError != NOERROR)<br>
 &nbsp; &nbsp; &nbsp; &nbsp;return (nError);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp;/* Get the DB Options */ &nbsp;<br>
 &nbsp; &nbsp;/* 1) Construct NetPath */<br>
 &nbsp; &nbsp;nError = OSPathNetConstruct (NULL, (char FAR *)szCanonServerName, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; pDBName, (char FAR *)szNetPathName);<br>
 &nbsp; &nbsp;if (nError != NOERROR) &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp; &nbsp;return nError;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* 2) Open the Database via NSFDbOpenExtended (support server failover)*/<br>
 &nbsp; &nbsp;nError = NSFDbOpenExtended ((char FAR *)szNetPathName, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;DBOPEN_CLUSTER_FAILOVER, NULLHANDLE, NULL,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;hDb, &amp;dataNoteMod, &amp;nonDataNoteMod );<br>
 &nbsp; &nbsp;if (nError != NOERROR )<br>
 &nbsp; &nbsp; &nbsp; &nbsp;return nError;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* 3) Check for clustered server failover by getting the path name of the<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;opened database */ &nbsp;<br>
 &nbsp; &nbsp;nError = NSFDbPathGet(hDb, (char FAR *)szFailoverPathName, NULL);<br>
 &nbsp; &nbsp;if (nError != NOERROR )<br>
 &nbsp; &nbsp; &nbsp; &nbsp;return nError;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* parsing out the server and database names */<br>
 &nbsp; &nbsp;nError = OSPathNetParse ((char FAR *)szFailoverPathName, NULL, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; (char FAR *)szFailoverServerName, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; (char FAR *)szFailoverDBName);<br>
 &nbsp; &nbsp;if (nError != NOERROR )<br>
 &nbsp; &nbsp; &nbsp; &nbsp;return nError;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* and comparing them to the specified parameters */<br>
 &nbsp; &nbsp;if (lstrcmpi((char FAR *)szCanonServerName, (char FAR *)szFailoverServerName))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;/* Failover occured -&gt; return new abbreviated server/db name */<br>
 &nbsp; &nbsp; &nbsp; &nbsp;*bFailover = TRUE;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;nError = DNAbbreviate (0L, NULL, (char FAR *)szFailoverServerName,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;pServerName, MAXUSERNAME, NULL);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;lstrcpy (pDBName, (char FAR *)szFailoverDBName);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;if (nError != NOERROR )<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;return nError;<br>
 &nbsp; &nbsp;}<br>
 &nbsp; &nbsp;else<br>
 &nbsp; &nbsp; &nbsp; &nbsp;*bFailover = FALSE;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* 4) Get the Database options via NSFDBGetOptions */<br>
 &nbsp; &nbsp;nError = NSFDbGetOptions (hDb, dwOptionMask);<br>
 &nbsp; &nbsp;if (nError != NOERROR )<br>
 &nbsp; &nbsp; &nbsp; &nbsp;return nError;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* 5) Close the Database and return */<br>
 &nbsp; &nbsp;nError = NSFDbClose (hDb);<br>
 &nbsp; &nbsp;return nError;<br>
}</font></tt>
---
