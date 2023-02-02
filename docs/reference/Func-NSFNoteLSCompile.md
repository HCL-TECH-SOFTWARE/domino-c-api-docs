##### Function : LotusScript
##### NSFNoteLSCompile - Compile a note containing LotusScript modules.
---
##### #include <nsfnote.h>
STATUS LNPUBLIC **NSFNoteLSCompile(**

	DBHANDLE  hDb,
	NOTEHANDLE  hNote,
	DWORD  dwFlags);
**Description :**
The API compiles all the LotusScript code found in a design document.  This 
includes document classes such as Views, Agents, Forms, Pages, Navigators, 
Shared fields,  script libraries, Help documents, using database documents, 
etc.  It is a way of making sure that the object code of the script is 
up-to-date.  

For the Agent note, the compiled object code is saved in the $AssistAction_Ex 
item.
**Parameters :**
Input :
hDb  -  Handle to the database.

hNote  -  Handle to the note containing LotusScript modules.

dwFlags  -  (Reserved for future use) Must be 0.


Output :
(routine)  -  (routine)  -  Return indicates either success or what the error is. The return codes include: 

NOERROR - Operation was successful.

ERR_NULL_NOTEHANDLE -  if hNote was not specified.

ERR_xxx - STATUS returned from a lower level Notes function call.


**Sample Usage :**
```
 
...
/*  Compile the Agent note */       
if (error=NSFNoteLSCompile(hDb,hAgent,0))
{
   printf("Error: LS Compile\n");
   goto Exit1;
}

/*  Update the note */
if (error=NSFNoteUpdate(hAgent,0))
{
   printf("Error: can't update note after LS Compile\n");
   goto Exit1;
}

```
**See Also :**
[](D:/md_files/.md)
---
