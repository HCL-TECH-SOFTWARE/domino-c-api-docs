##### Data Type : Signal Handler
##### OSSIGBUSYPROC - Function pointer template for Busy signal handler.
---
##### #include <ossignal.h>
**Description :**
Definition of a pointer to a function that will handle the Busy signal.  The 
default Busy signal handler displays an indicator on the status line when file 
or network activity is taking place.  The return value from this function is an 
error code if an error occurs, NOERROR otherwise.

This signal handler requires a single parameter:

    BusyType - Type of busy indicator to display;  use one of the 
BUSY_SIGNAL_xxx Symbolic Values.
**See Also :**
[BUSY_SIGNAL_xxx](D:/md_files/BUSY_SIGNAL_xxx.md)
[IXPostMessage](D:/md_files/IXPostMessage.md)
[OSGetSignalHandler](D:/md_files/OSGetSignalHandler.md)
[OSSetSignalHandler](D:/md_files/OSSetSignalHandler.md)
[OS_SIGNAL_xxx](D:/md_files/OS_SIGNAL_xxx.md)
---
