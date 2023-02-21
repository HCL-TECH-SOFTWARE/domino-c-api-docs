##### Function : Signal Handler
##### IXPostMessage - Place a text string in the Workstation's Status Bar.
---
```
#include <ixport.h>
void IXPostMessage(

	char far *str);
```
**Description :**

This MACRO provides a simple wrapper for OSGetSignalHandler, that allows you to 
place/post a null-terminated string in the message/status area of the Status 
Bar of the Lotus Notes workstation application.  This function can be used to 
provide OS independent status updates to the user.  This function should only 
be used in a GUI environment.  

#define IXPostMessage(str) \
(OSGetSignalHandler(OS_SIGNAL_MESSAGE) ? \
(*(OSSIGMSGPROC)OSGetSignalHandler(OS_SIGNAL_MESSAGE))(str,OSMESSAGETYPE_POST_NO
SERVER)\
 : NOERROR)

Note: You may wish to provide a suitable delay in your code during which, the 
user is able to absorb the contents of the message.  This is because the 
Workstation application may update the Status Bar as soon as your program 
relinquishes control.  The usual cause is a mail delivery notification message 
or some network broadcast.

**Parameters :**
Input :
str  -  A pointer to a null-terminated string containing the message you would like to display.

Output :
(routine)  -  None.



**Sample Usage :**
```
/* Open the Export file */
IXPostMessage("Begin writing the Export file.");
for (count = 0; count < 1048576; count++) /* Poor night's sleep */;
   hExpFile = OpenFile( FileName, &ExpOfStruct, OF_CREATE);
```
**See Also :**
[OSGetSignalHandler](/domino-c-api-docs/reference/Func/OSGetSignalHandler)
---
