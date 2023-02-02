##### Function : Server
##### NSGetServerList - Return a list of known servers on a given port.
---
##### #include <ns.h>
STATUS LNPUBLIC **NSGetServerList(**

	char far *pPortName,
	DHANDLE far *retServerTextList);
**Description :**
Given a port name, this function will return a handle to a list of known 
servers on that port.  The port name(s) may be determined by calling the 
function OSGetEnvironmentString to read the "Ports=" environment variable from 
notes.ini.  The caller is responsible for freeing the memory used for the 
server list by calling OSMemFree.

If no port name is provided (the first argument is NULL), a list of known 
servers on all ports will be returned.  An error on a port will cause this 
function to terminate with only the servers found up to that point in the list.

The list is obtained from the home/mail server's Domino Directory.
**Parameters :**
Input :
pPortName  -  A far pointer to a string containing the name of the network port.  Set this to NULL to return a list of known servers on all ports.

Output :
(routine)  -   Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


retServerTextList  -  A handle to a buffer containing a list of known servers on the specified network port.  The buffer consists of: 
      A WORD containing the number of server names in the list (we'll call it N); 
      A WORD array of of size N,  each entry specifying the length (without null terminator) of the corresponding server name;
      A packed list of N server names.

**Sample Usage :**
```
/* Get the list of available servers.  Setting the first parameter
    to NULL gets a list of known servers on all ports.
 */
         
sError = NSGetServerList( (char far *) NULL, &hServerList);
                                          
if (sError != NOERROR)
{
   return;
}

pServerList  = (BYTE far *)OSLockObject(hServerList);
wServerCount = (WORD) *pServerList;

pwServerLength = (WORD *)(pServerList + sizeof(WORD));

pServerName = (BYTE far *) pServerList + sizeof(wServerCount) +
                          ((wServerCount) * sizeof(WORD));

for (i=0; i<wServerCount; pServerName+=pwServerLength[i], i++)
{
   memmove (szServerString, pServerName, pwServerLength[i]);
   szServerString[pwServerLength[i]] = '\0'; 
   SendDlgItemMessage(hDlg, SERVLIST_LISTBOX, LB_ADDSTRING,
                     (WORD) NULL,  
                     (LONG)(LPSTR) szServerString);
}
OSUnlockObject (hServerList);
OSMemFree (hServerList);
```
**See Also :**
[OSGetEnvironmentString](D:/md_files/OSGetEnvironmentString.md)
---
