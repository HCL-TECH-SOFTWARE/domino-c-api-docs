##### Function : Server
##### NSFRemoteConsole - Issues a console command to a server.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFRemoteConsole(**

	char far *ServerName,
	char far *ConsoleCommand,
	DHANDLE far *hResponseText);
**Description :**
This function is used to issue a console command to a server from an API 
program or from an API server add-in program.  

If you do not have remote access to the server an error will be returned.  To 
have remote access to a server, you must be listed in the Server Document 
Administrators field or in the Admin variable in the server's notes.ini.

NOTE: If you use this function to shut down a server (by entering the "exit" or 
"quit" commands), you may receive an error code of "Server not responding" or 
"Remote system no longer responding".  Assuming that the server was active when 
you issued the command, these errors usually mean that your command was 
successful (the server shuts down before it can return a meaningful response).

NOTE:  This function will return NOERROR if the server's disk is full, but the 
returned response buffer will be 0-length. 
**Parameters :**
Input :
ServerName  -  Pointer to the name of the server that is to receive the console command.

ConsoleCommand  -  Pointer to the text command to send to the server's console.

Output :
(routine)  -   Return status from this call -- indicates either sucess or what the error is. The return codes include:

NOERROR - no error.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user.


hResponseText  -  Pointer to handle of a buffer containing the returned server's response.  Use OSLock to obtain a pointer to this buffer.  The buffer will be NULL terminated.  After processing the returned buffer, use OSUnlock to unlock the buffer pointer and OSMemFree to free the memory associated with this handle.

**Sample Usage :**
```

DHANDLE hRetInfo;
STATUS nError;
char *pBuffer;

nError = NSFRemoteConsole ("MARKETING", "SHOW TASKS", &hRetInfo);
if (nError != NOERROR)
   return (ERR(nError));

/* Lock the returned buffer handle to obtain a pointer to the
   text buffer containing the server command information */

pBuffer = OSLock (char, hRetInfo);

printf(pBuffer);

OSUnlock (hRetInfo);

OSMemFree (hRetInfo);

return (NOERROR);

```
**See Also :**
[](D:/md_files/.md)
---
