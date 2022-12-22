




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




 


**Function : Item (Field)**



**NSFItemAppendObject** **- Add an
object item (field of type TYPE\_OBJECT) to a note.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFItemAppendObject(**  

      NOTEHANDLE  hNote,  

      WORD  ItemFlags,  

      const char far \*Name,  

      WORD  NameLength,  

      BLOCKID  bhValue,  

      DWORD  ValueLength,  

      BOOL  fDealloc**);**



**Description :**



Add an item
of TYPE\_OBJECT to an existing note. You must use NSFItemAppendObject to append
an item of TYPE\_OBJECT to a note rather than NSFItemAppend, because
NSFItemAppendObject copies certain information from the item value to the
Domino internal item descriptor.  

  

An object item consists of two parts: the object itself in the database, and
the object item in the note. The object itself resides in the Domino database
file at a location identified by it's RRV (a.k.a. Object ID). Use the
NSFDbAllocObject family of functions to manipulate the object itself.  The
object item is a structure of type OBJECT\_DESCRIPTOR that resides in a note.
The RRV member of the OBJECT\_DESCRIPTOR identifies the location of the object
data in the Domino database file.  

  

Domino and Notes uses objects to store data that is not rendered on the screen
by the Notes editor. Examples include file attachments ($FILE fields), help
indexes, and macro left-to-do lists ($LeftToDo fields). For file attachments,
NSFNoteAttachFile is simpler to use than NSFItemAppendObject.  

  

Add an object item to a note by allocating space for the object itself in the
database, then appending the object item to the note. Call NSFDbAllocObject to
allocate space for the object and to obtain the RRV (Object ID) of the object.
Initialize the RRV member of an OBJECT\_DESCRIPTOR structure with this object
ID. Next, initialize an item value buffer to append to the note. The item value
buffer must start with the data type word (TYPE\_OBJECT) followed by the
OBJECT\_DESCRIPTOR structure.   Call NSFItemAppendObject() to add the item
buffer to the note.  You must unlock the block containing the item buffer
before you call NSFItemAppendObject.   

  

NSFItemAppendObject transfers ownership of the item buffer to the note. After
successful return from NSFItemAppendObject, do not free the item buffer.


 


**Parameters :**



Input :  

hNote  -  The handle to the note that will receive the object item.  

  

ItemFlags  -  The flags that define the characteristics of this item. These
flags are defined in ITEM\_xxx and may be bit-wise - OR'ed together for combined
functionality. Normally, use ITEM\_SUMMARY for items of type TYPE\_OBJECT.  

  

Name  -  Field name of the item in the note. Normally, use one of the symbolic
values defined in STDNAMES.H such as VIEW\_COLLECTION\_ITEM or
FILTER\_LEFTTODO\_ITEM.  

  

NameLength  -  Length, in bytes, of the specified Name string. Do not count the
zero terminator, if present.  

  

bhValue  -  Specifies a Domino memory block containing the item value. This
value must begin with the data type word (which must be TYPE\_OBJECT for an
object item) followed by a structure of type OBJECT\_DESCRIPTOR. For portability
to non-Intel platforms, the data type word must be in Host format, but the
OBJECT\_DESCRIPTOR structure must be converted to Domino Canonical Format. The
memory block must be unlocked. NSFItemAppendObject transfers ownership of the
memory block to the note. Do not free this memory block after successful
return.  

  

ValueLength  -  The length, in bytes, of the item value. This length must
include the length of the data type word.  

  

fDealloc  -  TRUE if object (specified by the RRV member of the
OBJECT\_DESCRIPTOR) should be de-allocated by Domino or Notes when the note is
de-allocated or the object item is deleted. FALSE gives the object persistence
beyond that of the object item. Normally, you should specify TRUE.  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Successfully appended object item to the note.  

  

ERR\_xxx - Errors returned by lower level Notes functions.  Call to OSLoadString
to interpret the error code for display.  

  

  




 **Sample Usage :**


BYTE       \*pb;  

WORD       \*pw;  

DWORD       dwObjectID;  

OBJECT\_DESCRIPTOR   objLeftToDo;  

OBJECT\_DESCRIPTOR  \*pobj;  

BLOCKID     bidLeftToDo;  

DWORD       dwItemSize;  

  

if (error = NSFDbAllocObject(hDb, dwObjectSize, NOTE\_CLASS\_DOCUMENT, 0,   

                            &dwObjectID))  

{  

   printf ("Error: unable to allocate LeftToDo Object.\n");  

   goto Exit1;  

}  

      

objLeftToDo.ObjectType =  OBJECT\_FILTER\_LEFTTODO ;  

objLeftToDo.RRV = dwObjectID;  

  

dwItemSize = (DWORD) (sizeof(WORD) + sizeof(OBJECT\_DESCRIPTOR));  

  

if (error = OSMemAlloc(0, dwItemSize, &(bidLeftToDo.pool)))  

{  

   printf("Error: unable to allocate %ld bytes for LeftToDo item.\n",  

                            dwItemSize);  

   NSFDbFreeObject(hDb, dwObjectID);  

   goto Exit1;  

}  

  

bidLeftToDo.block = NULLHANDLE;  

  

pw = OSLockBlock(WORD, bidLeftToDo);  

\*pw = TYPE\_OBJECT;  

pw++;  

  

ODSWriteMemory (&pw, \_OBJECT\_DESCRIPTOR, &objLeftToDo, 1);  

      

OSUnlockBlock(bidLeftToDo);  

  

if (error = NSFItemAppendObject(hMacro, ITEM\_SUMMARY,  

                            FILTER\_LEFTTODO\_ITEM,   

                            sizeof(FILTER\_LEFTTODO\_ITEM)-1,  

                            bidLeftToDo,   

                            dwItemSize,   

                            TRUE)) /\* Notes will deallocate memory \*/  

{  

   printf ("Error: unable to append %s item.\n",


                           
FILTER\_LEFTTODO\_ITEM);  

   OSMemFree(bidLeftToDo.pool);  

   goto Exit1;  

}


 **See Also :**


**[ITEM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/00F200B70087008C85255E2D007931E6)**


**[NSFDbAllocObject](NSFDbAllocObject.md)**


**[NSFDbWriteObject](NSFDbWriteObject.md)**


**[OBJECT\_DESCRIPTOR](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/004700B10077000185255EA0006A8D0C)**



----------------------------------------------------------------------------------------------------------


 





