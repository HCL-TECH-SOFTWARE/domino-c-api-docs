##### Data Type : Signal Handler
##### OSSIGDIALPROC - Function pointer template for Dial signal handler.
---
##### #include <ossignal.h>
**Description :**
Definition of a pointer to a function that will handle the Dial signal.  The 
default Dial signal handler displays a dialog box allowing the user to specify 
options for dialing.  The return value from this function is ERR_NET_CONTINUE 
if dialing is to continue, an error code if an error occurs, NOERROR otherwise.

An application may use OSSetSignalHandler to redefine this signal handler in 
order to do some processing prior to dialing out. For example, the signal 
handler may warn the user that a call is about to be made and alow the user to 
continue or cancel. The user-defined handler should return ERR_NET_CONTINUE to 
continue with the call or any other error code to cancel the call. The API 
function (such as NSFDbOpen) which initiated the call will receive the signal 
handler's returned error code.

This signal handler requires five parameters:

    pServer - Far pointer to a null-terminated string containing the name of 
the server to dial.
            May be NULL.

    pPort - Far pointer to a null-terminated string containing the name of the 
port to use.
            May be NULL.

    pDialParams - Reserved for future use; should be set to NULL.

    pRetServer - Pointer to a buffer where the actual name of the server to be 
called is to be placed.
            May be NULL if this information is not needed.

    pRetPort - Pointer to a buffer where the actual name of the port to be used 
is to be placed.
            May be NULL if this information is not needed.
**See Also :**
[IXPostMessage](D:/md_files/IXPostMessage.md)
[OSGetSignalHandler](D:/md_files/OSGetSignalHandler.md)
[OSSetSignalHandler](D:/md_files/OSSetSignalHandler.md)
[OS_SIGNAL_xxx](D:/md_files/OS_SIGNAL_xxx.md)
---
