##### Data Type : Signal Handler
##### OSSIGBREAKPROC - Function pointer template for Check Break signal handler.
---
##### #include <ossignal.h>
**Description :**
Definition of a pointer to a function that will handle the Check Break signal.  
The default Check Break signal handler returns ERR_CANCEL if the user has 
issued a Break to interrupt network I/O, and NOERROR otherwise.  This signal 
handler requires no parameters.
**See Also :**
[IXPostMessage](D:/md_files/IXPostMessage.md)
[OSGetSignalHandler](D:/md_files/OSGetSignalHandler.md)
[OSSetSignalHandler](D:/md_files/OSSetSignalHandler.md)
[OS_SIGNAL_xxx](D:/md_files/OS_SIGNAL_xxx.md)
---
