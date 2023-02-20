##### Chapter 13-1
##### Advanced Services API Features

The HCL Domino Advanced Services lets you extend your Domino server configuration to include three advanced features:
<p>
<ul type="disc">
<li>Domino server clusters
<li>Partitioned servers
<li>Domino billing</ul>

<p>In HCL Notes/Domino 6, Domino server clusters must run the Domino 6 license, Release 5 or Release 4.62 Enterprise Server license, or the Domino Release 4.5 or Release 4.6 Advanced Services license.
<p>In Notes/Domino 6, partitioned servers are available only if you install the Partitioned Server.
<p>In Notes/Domino 6, you can enable billing on a Domino Server.
<p>
<p><b>Domino Server Clusters</b>
<p>A cluster is a group of up to six Domino servers in the same domain connected by a local area network (LAN). Clusters serve large enterprise and service-based infrastructures that support large numbers of users and provide high availability of data. The following cluster functions and symbols are available in the HCL C API toolkit for Domino and Notes:
<p>	NSFDbCreateAndCopy	NSGetServerClusterMates
<p>	NSFDbMarkForDelete	NSPingServer
<p>	NSFDbMarkInService	CLUSTER_LOOKUP_xxx
<p>	NSFDbMarkOutOfService
<p>
<p><b>Partitioned Servers</b>
<p>A partitioned server shares the resources of a single computer with other Domino servers. You can run multiple partitioned servers on a single computer. 
<p>In a partitioned server environment, each server has its own data directory but shares the same executable directory.  
<p>No further setup is needed to run a Domino C API server application.  The server application runs under the same environment as the server.
<p>However, a C API standalone application running on a computer with partitioned servers must be able to locate both the notes.ini file (found in the data directory) and the executable directory.  In order to run a C API standalone application on a computer with partitioned servers:
<ul type="disc">
<li>Change the current directory to the directory containing the notes.ini file before running the program </ul>
	or
<ul type="disc">
<li>For the current process ONLY, include the data directory in the path before invoking the C API standalone program.  This can be done by executing a SET PATH statement which must be executed only in the current process.  Do not put the data directory on the permanent path.</ul>

<p><b>Domino Billing</b>
<p>The Domino billing feature enables a Domino server to track specific Domino activities. The billing server task collects this information and records the data for billing purposes. The following billing data structures, functions, and symbols are available in the HCL C API Toolkit for Domino and Notes:
<p>	AGENTREC	BillingGetClass
<p>	BILLMSG	BillingWrite
<p>	BILLREC	BILLCHARGExxx
<p>	DBREC	BILL_AGENT_xxx
<p>	DOCUMENT	BILL_CLASS_xxx
<p>	MAILREC	BILL_QUEUE_NAME
<p>	REPLREC	BILL_xxx(actions)
<p>	SESSIONREC	BILL_xxx(structure types)
<p>
<p>These three features are described in the <i>Domino Administration Help </i>documentation.
---
