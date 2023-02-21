##### Function : AddIn
##### AddInSetStatusLine - Set the status string in the specified status line
---
```
#include <addin.h>
void LNVARARGS AddInSetStatusLine(

	DHANDLE  hDesc,
	char far *String,
	<Any 'C' type>  optional_var1, ...);
```
**Description :**

This function formats a string and sets the status string of the specified 
status line to the formatted string.  This function is only supported within 
the context of a server add-in.

A status line is one line of text displayed by the Domino server console in 
response to the "show tasks" command.  Each status line consists of a task name 
(in the left column) and a status string (in the right column).  The String 
input parameter to AddInSetStatusLine becomes the status string in the right 
column of the status line.

Server add-in tasks may create multiple status lines. The Lotus Domino Server 
"show tasks" command displays all status lines. Domino creates a default status 
line for add-in tasks that use AddInMain() as the main entry point.  Add-in 
tasks that do not use AddInMain() as the main entry point may optionally create 
a default status line.  Use AddInSetStatus() or  AddInSetStatusText() to change 
the status string in the default status line.  If you create non-default status 
lines using AddInCreateStatusLine(), you must use  AddInSetStatusLine() to set 
the status text part of these status lines.

The hDesc input argument must specify a status line descriptor handle.  Obtain 
this handle from AddInCreateStatusLine().  The String input argument may 
contain printf-style (%) format specifiers.  This function accepts from zero to 
12 bytes of additional parameters to resolve the format specifiers in String.  
Pointers passed in these arguments must be "far" pointers.  The print format 
specifiers supported by Domino are described in the Tech Note "Domino Print 
Format Specifiers".  Tech Notes are listed in the view, Reference Tools/Tech 
Notes.

**Parameters :**
Input :
hDesc  -  Status line descriptor handle. Obtain this handle from AddInCreateStatusLine(). 

String  -  String to format the status string. This may contain printf-style format specifiers.  If so, subsequent arguments must be provided to resolve these format specifiers.

optional_var1, ...  -  From 0 to 12 bytes of additional bytes of parameters to resolve the format specifiers in String.  All pointer values must be "far".



**Sample Usage :**
```

hSourceHostStatusLine = AddInCreateStatusLine ("Source Host Status");
hDestHostStatusLine = AddInCreateStatusLine ("Dest Host Status");

if (ConnectToHost(SourceHostName) == NOERROR)
{
    AddInSetStatusLine (hSourceHostStatusLine, "Connected");
}
else
{
    AddInSetStatusLine (hSourceHostStatusLine, "Disconnected");
}

if (ConnectToHost(DestinationHostName) == NOERROR)
{
    AddInSetStatusLine (hDestHostStatusLine, "Connected");
}
else
{
    AddInSetStatusLine (hDestHostStatusLine, "Disconnected");
}


```
**See Also :**
[AddInCreateStatusLine](/domino-c-api-docs/reference/Func/AddInCreateStatusLine)
[AddInDeleteStatusLine](/domino-c-api-docs/reference/Func/AddInDeleteStatusLine)
---
