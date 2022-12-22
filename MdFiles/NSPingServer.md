




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



**Function : Clusters**



**NSPingServer** **- Attempt
to detect if a server is reachable.**


**----------------------------------------------------------------------------------------------------------**



**#include <ns.h>**



STATUS
LNPUBLIC **NSPingServer(**  

      char far \*pServerName,  

      DWORD far \*pdwIndex,  

      DHANDLE far \*phList**);**



**Description :**



The
NSPingServer function determines if a Lotus Domino Server is reachable.  In
addition this function optionally retrieves the specified server's workload
index (if any), the name of the cluster (if any) to which the server belongs,
and a list (of type TEXT\_LIST), all members in the server cluster including the
specified server.  If the server is in a BUSY state, the return status is set
to ERR\_SERVER\_UNAVAILABLE.   If the server has been restricted by the system
administrator, the return status is set to ERR\_SERVER\_RESTRICTED.   In either
state, the server continues to return its availability index and cluster member
list if the pdwIndex and phList parameters are not NULL.  


 


      If
specified as non-NULL on input, the pdwIndex parameter contains the server's
current availability index.  This index is a value from 0 - 100.  The index
value is compared with the SERVER\_AVAILABILITY\_THRESHOLD value that is set by
the server administrator at the console, or in the server notes.ini file.  If
the availability index falls below the value specified by
SERVER\_AVAILABILITY\_THRESHOLD, then the server enters a BUSY state.  In this
state, the server does not allow newclient sessions to be established.  The
server continues to maintain existing client sessions and replication
activities when BUSY.  


 


Similar
behavior occurs if a server is RESTRICTED. An administrator can place a server
in a RESTRICTED state by setting  SERVER\_RESTRICTED=1 in the server notes.ini
file. Servers that do not participate in workload balancing (such as, R3
servers or non-cluster members) always return 0 if this item is requested.  In
addition, if the phList parameter is specified as non-Null on input, the name
of the cluster to which the server belongs and a complete list of other cluster
members is returned if the function is successful and the input server is a
member of a Domino cluster.   If the list is non-Null on return then the first
entry (position 0) contains the name of the cluster to which the server
belongs.  The remaining entries (if any) contain the names of the server
members that are part of the cluster, including the specified input server. 
The caller should lock the returned list down using the OSLockObject function
before processing the list and unlock it with OSUnLockObject when processing is
completed.  Use the ListGetNumEntries function to determine the number of
entries in the returned list.  Use the ListGetText function to retrieve the
individual components of the list.   The returned list is sorted by workload
level, and lists the server with the least workload first.


 


      For
more information about managing database availability in a cluster, TCP/IP port
mapping, and workload balancing, see the *Domino Administration Help* database.


 


**Parameters :**



Input :  

pServerName  -  Address of null-terminated target server name string
(required).   For partitioned, clustered servers that are accessed through a
configured TCP/IP port mapping,  the server name must be distinguished and in
canonical format.   Otherwise, a server access error will be returned.   All
other server names can be in abbreviated format.  

  

pdwIndex  -  Address of location to store load index of pServerName
(optional).  Specify NULL for this argument if you do not wish the server's
availability index to be returned.  

  

phList  -  Address of location to store handle to TEXT\_LIST of cluster name
followed by one or more names of servers in cluster (optional).  Specify NULL
for this argument if you do not wish the list to be returned.  

  




Output :  

(routine)  -  If server is reachable, NOERROR;  

If server is busy, ERR\_SERVER\_UNAVAILABLE;  

If server is restricted, ERR\_SERVER\_RESTRICTED;  

Otherwise, one of a number of possible ERR\_xxx errors.  

  

  

pdwIndex  -  If non-NULL on input, will contain the load index of the target
server (i.e., 0-100 where 100 is the least loaded value).  A value of zero  and
a return status of zero will indicate that the server does not participate in
load balancing.  

  

phList  -  If non-NULL on input, will contain a HANDLE to a TEXT\_LIST of
cluster name followed by one or more server names which are members of the
cluster in which 'pServerName' is participating, if any.  Output of NULLHANDLE
and a function return status of zero indicates the 'pServerName' is not a
member of a cluster.  The caller is responsible for freeing the memory
associated with the list if this parameter is Non-NULL.  

  




 **Sample Usage :**


#include <ns.h>


 


{


   STATUS error =
NOERROR;  

   DHANDLE hList = NULLHANDLE;


   DWORD  dwLoadIndex =
0;


   char   \*pServerName
= "elvis/iris";


 


   /\* Check for load
and/or cluster members, if any \*/


 


   error =
NSPingServer(pServerName, &dwLoadIndex, &hList);                          

   if (!error || ERR(error) == ERR\_SERVER\_UNAVAILABLE)  

   {


     
printf("Server '%s' load index = %ld.\n", pServerName, dwLoadIndex);


 


      if (hList ==
NULLHANDLE)


        
printf("Server '%s' is not a member of any cluster.\n", 
pServerName);


      else


      {  

         char \*pBuffer;   

         char Buffer[MAXUSERNAME];  

         WORD BufferLength;  

         WORD i;  

         WORD NumListEntries;  

         void far \*lpList;


 


         lpList =
OSLock(void, hList);  

         NumListEntries = ListGetNumEntries(lpList, FALSE);  

         if (NumListEntries > 0)  

         {  

            /\* first entry is the cluster name \*/


            error =
ListGetText(lpList, FALSE, 0, &pBuffer, &BufferLength);  

            {  

               strncpy(Buffer, pBuffer, BufferLength);  

               Buffer[BufferLength] = '\0';


 


               printf("Server
'%s' is a member of the '%s' cluster.\n",


                                  pServerName,
Buffer);  

            }


                                  


            /\* iterate
through cluster members and pinging each


                          to
determine reachability/availability \*/


  

            for (i = 1; i < NumListEntries; i++)  

            {  

               error = ListGetText(lpList, FALSE, i, &pBuffer,
&BufferLength);  

               if (!error)  

               {  

                  strncpy(Buffer, pBuffer, BufferLength);  

                  Buffer[BufferLength] = '\0';


  

                  /\*ping the cluster member \*/


                  error
= NSPingServer(Buffer, (DWORD \*)NULL, (char \*)NULL);


                  if
(!error)


                    
printf("Server '%s' is reachable.\n", Buffer);


  

                  if (ERR(error) == ERR\_SERVER\_UNAVAILABLE)  

                     printf("Server '%s' is busy.\n", Buffer);


  

                  if (ERR(error) == ERR\_SERVER\_RESTRICTED)  

                     printf("Server '%s' is restricted.\n", Buffer);  

               }  

            }  

         }  

  




     
OSUnlockObject(hList);  

      }


   }


 


   /\* release temporary
server text list resources \*/  

   if (hList != NULLHANDLE)  

      OSMemFree(hList);  

  




   return error;


}


 **See Also :**


**[ListGetNumEntries](ListGetNumEntries.md)**


**[ListGetText](ListGetText.md)**


**[NSGetServerClusterMates](NSGetServerClusterMates.md)**


**[OSLockObject](OSLockObject.md)**


**[OSMemFree](OSMemFree.md)**


**[OSUnlockObject](OSUnlockObject.md)**



----------------------------------------------------------------------------------------------------------


 





