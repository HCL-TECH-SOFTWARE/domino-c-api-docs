




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




 


**Function : Database**



**NSFDbAllocObject** **- Allocates
an object in a Domino database file.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfobjec.h>**



STATUS
LNPUBLIC **NSFDbAllocObject(**  

      DBHANDLE  hDB,  

      DWORD  dwSize,  

      WORD  Class,  

      WORD  Privileges,  

      DWORD far \*retObjectID**);**



**Description :**



Allocate
space for an object in an open database file. This reserves space in the
database file for the object data itself and returns the object ID.  

  

The object ID (the RRV) identifies the location of the object in the database
file. You need this object ID in subsequent calls to NSFDbWriteObject, etc.
Store this object ID in the RRV member of the OBJECT\_DESCRIPTOR structure.
Store the OBJECT\_DESCRIPTOR structure in an item of type TYPE\_OBJECT that you
append to a note.   

  

Domino and Notes uses objects and object items to store data that is not
rendered on the screen by the Notes editor. Examples include file attachments
($FILE fields), help indexes, and macro left-to-do lists ($LeftToDo). Note that
for file attachments, NSFNoteAttachFile is simpler to use than
NSFItemAppendObject.  

  

An object item consists of two parts: the object itself in the database, and
the object item in the note. The object itself resides in the Domino database
file at a location identified by it's RRV (the Object ID). Use NSFDbAllocObject
to allocate space for the object itself.  The object item is a structure of
type OBJECT\_DESCRIPTOR that resides in a note. Use NSFItemAppendObject to
append the object item to a note.  

  

Create an object by first creating the object itself in the database, then
appending an object item to the note. Read an object by reading the object item
in the note, obtaining the RRV of the object, then calling NSFDbReadObject
specifying the RRV you obtained from the item.


 


**Parameters :**



Input :  

hDB  -  Handle to the open database in which to allocate the object  

  

dwSize  -  Size in bytes of the object data  

  

Class  -  Object class. Normally, set this to NOTE\_CLASS\_DOCUMENT.  Domino and
Notes uses the same classes for objects as for notes. See NOTE\_CLASS\_xxx.  

  

Privileges  -  Privilege mask controlling access to this object. Specify zero
if not used.  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Successfully appended Item to the note.  

  

ERR\_xxx - Errors returned by lower level functions. Call OSLoadString to obtain
a string to display to the user.  

  

  

retObjectID  -  The specified variable receives the Object ID of the object in
the database. Use this object ID to refer to this object in subsequent calls to
NSFDbWriteObject, etc. Store this object ID in the RRV member of the
OBJECT\_DESCRIPTOR structure.  

  




 **Sample Usage :**


  

    if (error = NSFDbAllocObject(hDb, dwObjectSize, NOTE\_CLASS\_DOCUMENT, 0,   

                                &dwObjectID))  

    {  

        printf ("Error: unable to allocate LeftToDo Object.\n");  

        goto Exit1;  

    }  

      

    objLeftToDo.ObjectType = OBJECT\_FILTER\_LEFTTODO ;  

    objLeftToDo.RRV = dwObjectID;  

  




 **See Also :**


**[NOTE\_CLASS\_xxx](NOTE_CLASS_xxx.md)**


**[NSFDbFreeObject](NSFDbFreeObject.md)**


**[NSFDbGetObjectSize](NSFDbGetObjectSize.md)**


**[NSFDbReadObject](NSFDbReadObject.md)**


**[NSFDbReallocObject](NSFDbReallocObject.md)**


**[NSFDbWriteObject](NSFDbWriteObject.md)**


**[NSFItemAppendObject](NSFItemAppendObject.md)**


**[OBJECT\_DESCRIPTOR](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/004700B10077000185255EA0006A8D0C)**



----------------------------------------------------------------------------------------------------------


 





