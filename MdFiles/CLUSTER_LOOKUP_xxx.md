




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
 /\* Style Definitions \*/
 p.MsoNormal, li.MsoNormal, div.MsoNormal
 {margin-top:0cm;
 margin-right:0cm;
 margin-bottom:8.0pt;
 margin-left:0cm;
 line-height:107%;
 font-size:11.0pt;
 font-family:"Calibri",sans-serif;}
.MsoChpDefault
 {font-size:11.0pt;}
.MsoPapDefault
 {margin-bottom:8.0pt;
 line-height:107%;}
 /\* Page Definitions \*/
 @page WordSection1
 {size:612.0pt 792.0pt;
 margin:72.0pt 72.0pt 72.0pt 72.0pt;}
div.WordSection1
 {page:WordSection1;}
-->




**Initial Release 4.0**



**Symbolic Value : Clusters**



**CLUSTER\_LOOKUP\_xxx** **-** IBM Domino
Server Cluster Lookup Flags


**----------------------------------------------------------------------------------------------------------**



**#include <ns.h>**


 **Symbolic Values :**      CLUSTER\_LOOKUP\_NOCACHE      -  Instructs the
NSGetServerClusterMates function to not use the cluster name cache and forces a
lookup on the target server instead  

  

      CLUSTER\_LOOKUP\_CACHEONLY   -  Instructs the NSGetServerClusterMates
function to only use the cluster name cache and restricts lookup to the
workstation cache  

  




**Description :**



These values
are used as input to the NSGetServerClusterMates function.  When you specify
the CLUSTER\_LOOKUP\_NOCACHE value, the call retrieves the input server's cluster
member list through a NameLookup on the input server.  The client cluster cache
is not used for determining this information.  


 


      When
you specify the CLUSTER\_LOOKUP\_CACHEONLY value, the call is forced to retrieve
the server's cluster member list from the local client cluster cache.  There is
no NameLookup performed on the server in this case.


 **Sample Usage :**


/\* Given a server name,
get the cluster mates from the cluster cache and from the server \*/


 


#include <ns.h>


 


STATUS error;


HANDLE hClusterMateList
= NULLHANDLE;


 


/\* get clustermate
information only from local client's cluster name cache \*/


error =
NSGetServerClusterMates(ServerName, CLUSTER\_LOOKUP\_CACHEONLY,
&hClusterMateList);


 


if (hClusterMateList !=
NULLHANDLE)


  
OSMemFree(hClusterMateList);


 


hClusterMateList = NULLHANDLE;


 


/\* get clustermate
information only through a NameLookup on the server \*/


error =
NSGetServerClusterMates(ServerName, CLUSTER\_LOOKUP\_NOCACHE,
&hClusterMateList);


 


if (hClusterMateList !=
NULLHANDLE)


  
OSMemFree(hClusterMateList);


 **See Also :**


**[NSGetServerClusterMates](NSGetServerClusterMates.md)**



----------------------------------------------------------------------------------------------------------


 





