




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Function : Server**



**NSGetServerList** **- Return a
list of known servers on a given port.**


**----------------------------------------------------------------------------------------------------------**



**#include <ns.h>**



STATUS
LNPUBLIC **NSGetServerList(**  

      char far \*pPortName,  

      DHANDLE far \*retServerTextList**);**



**Description :**



Given a port
name, this function will return a handle to a list of known servers on that
port.  The port name(s) may be determined by calling the function
OSGetEnvironmentString to read the "Ports=" environment variable from
notes.ini.  The caller is responsible for freeing the memory used for the
server list by calling OSMemFree.


 


If no port
name is provided (the first argument is NULL), a list of known servers on all
ports will be returned.  An error on a port will cause this function to
terminate with only the servers found up to that point in the list.


 


The list is
obtained from the home/mail server's Domino Directory.


 


**Parameters :**



Input :  

pPortName  -  A far pointer to a string containing the name of the network
port.  Set this to NULL to return a list of known servers on all ports.  

  




Output :  

(routine)  -   Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

retServerTextList  -  A handle to a buffer containing a list of known servers on
the specified network port.  The buffer consists of:   

      A WORD containing the number of server names in the list (we'll call it
N);   

      A WORD array of of size N,  each entry specifying the length (without
null terminator) of the corresponding server name;  

      A packed list of N server names.  

  




 **Sample Usage :**


/\* Get the list of
available servers.  Setting the first parameter  

    to NULL gets a list of known servers on all ports.  

 \*/  

           

sError = NSGetServerList( (char far \*) NULL, &hServerList);  

                                            

if (sError != NOERROR)  

{  

   return;  

}  

  

pServerList  = (BYTE far \*)OSLockObject(hServerList);  

wServerCount = (WORD) \*pServerList;  

  

pwServerLength = (WORD \*)(pServerList + sizeof(WORD));  

  

pServerName = (BYTE far \*) pServerList + sizeof(wServerCount) +  

                          ((wServerCount) \* sizeof(WORD));  

  

for (i=0; i<wServerCount; pServerName+=pwServerLength[i], i++)  

{  

   memmove (szServerString, pServerName, pwServerLength[i]);  

   szServerString[pwServerLength[i]] = '\0';   

   SendDlgItemMessage(hDlg, SERVLIST\_LISTBOX, LB\_ADDSTRING,  

                     (WORD) NULL,    

                     (LONG)(LPSTR) szServerString);  

}  

OSUnlockObject (hServerList);  

OSMemFree (hServerList);


 **See Also :**


**[OSGetEnvironmentString](OSGetEnvironmentString.md)**



----------------------------------------------------------------------------------------------------------


 





