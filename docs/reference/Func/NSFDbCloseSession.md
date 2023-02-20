##### Function : Database
##### NSFDbCloseSession - Close an open database and the session to the server.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbCloseSession(

	DBHANDLE  hDB);
```
**Description :**

This function closes an open database.  Also, if the database resides on a 
remote server and if there are no other programs on the computer that have 
opened any other databases on that remote server, then NSFDbCloseSession closes 
the session to the server, as well.  If NSFDbCloseSession does close the 
session, and if it is a modem dial-up connection, and if the connection was 
originally established using Notes (as opposed to being established outside of 
Notes), then NSFDbCloseSession also hangs up the phone call.

NSFDbCloseSession is an alternative entry point of the NSFDbClose function and 
is provided as a convenience to users of the C API.  If your program is 
responsible for hanging up a dial-up connection immediately after the last 
database on the remote server is closed, there are two options.  You can simply 
use NSFDbCloseSession to close databases.  Alternatively, you can call 
NSFDbClose to close databases, but you will also need to keep track of when the 
program closes the last database it opened on the remote server and then call 
NetCloseSession explicitly to force a hangup.  If you do not want to hang up a 
connection to a remote server after closing the last opened database, you 
should always use NSFDbClose to close a database instead of using 
NSFDbCloseSession.

**Parameters :**
Input :
hDB  -  The handle to the open database.

Output :
(routine)  -  Return status of the call - indicates either success or what the error is. The return codes include:

NOERROR

ERR_xxx - Error returned by lower level functions. Call OSLoadString to interpret the code.



**Sample Usage :**
```
if (error = NSFDbCloseSession (hDB))
{
     goto Exit;
}
```
**See Also :**
[DBHANDLE](/reference/Data/DBHANDLE)
[NSFDbClose](/reference/Func/NSFDbClose)
[NSFDbOpen](/reference/Func/NSFDbOpen)
---
