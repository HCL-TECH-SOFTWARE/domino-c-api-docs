




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




 


**Data Type : Item (Field) Information**



**OBJECT\_DESCRIPTOR** **-** Object item
strucure


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfdata.h>**



**Definition :**



typedef struct {  

   WORD  ObjectType;  /\* Type of object (OBJECT\_xxx) \*/  

   DWORD RRV;         /\*Object ID of the object in THIS FILE \*/  

} OBJECT\_DESCRIPTOR;


 


**Description :**



All items
(fields) of type TYPE\_OBJECT contain this data structure.  

  

Domino and Notes use objects to store data that is not rendered on the screen
by the Notes editor. Examples include file attachments ($FILE fields), help
indexes, and macro left-to-do lists ($LeftToDo fields).   

  

The ObjectType member stores the type of the object. The RRV member stores the
ID that identifies the object in the database.  

  

An object consists of two parts: the object itself in the database, and the
object item in the note. The object itself is stored separately from the note
and is identified by it's Object ID (the RRV). The object item is a structure
of type OBJECT\_DESCRIPTOR that resides in the note. The RRV member of the
OBJECT\_DESCRIPTOR identifies the object itself in the Domino database file.   

  

Possible object types include OBJECT\_FILE and OBJECT\_FILTER\_LEFTTODO. See
OBJECT\_xxx for a list of all object types. For file attachments ($FILE fields)
the ObjectType member is OBJECT\_FILE. In this case, the OBJECT\_DESCRIPTOR
serves as the header for the larger FILEOBJECT structure.  

  

To attach a file to a note, use NSFNoteAttachFile. To add a different type of
object to a note, use NSFDbAllocObject() and NSFItemAppendObject().


 **Sample Usage :**


    OBJECT\_DESCRIPTOR  
objLeftToDo;  

    OBJECT\_DESCRIPTOR  \*pobj;  

    BLOCKID     bidLeftToDo;    

  

    /\* Assume Windows platform. Code below must  

       be modified to convert the OBJECT\_DESCRIPTOR to  

       Domino Canonical Format in order to be portable.  

     \*/  

  

    objLeftToDo.ObjectType = OBJECT\_FILTER\_LEFTTODO ;  

    objLeftToDo.RRV = dwObjectID;  

  

    dwItemSize = (DWORD) (sizeof(WORD) + sizeof(OBJECT\_DESCRIPTOR));  

  

    if (error = OSMemAlloc(0, dwItemSize, &(bidLeftToDo.pool)))  

    {  

        printf ("Error: unable to allocate %ld bytes for LeftToDo
item.\n",  

                                    dwItemSize);  

        NSFDbFreeObject(hDb, dwObjectID);  

        goto Exit1;  

    }  

  

    bidLeftToDo.block = NULLHANDLE;  

  

    pw = OSLockBlock(WORD, bidLeftToDo);  

    \*pw = TYPE\_OBJECT;  

    pw++;  

    pobj = (OBJECT\_DESCRIPTOR\*)pw;  

    \*pobj = objLeftToDo;  

    OSUnlockBlock(bidLeftToDo);  

  

    if (error = NSFItemAppendObject(hMacro, ITEM\_SUMMARY,  

                            FILTER\_LEFTTODO\_ITEM,   

                            sizeof(FILTER\_LEFTTODO\_ITEM)-1,  

                            bidLeftToDo,   

                            dwItemSize,   

                            TRUE))      /\* Notes will deallocate memory \*/  

    {  

        printf ("Error: unable to append %s item.\n",
FILTER\_LEFTTODO\_ITEM);  

        OSMemFree(bidLeftToDo.pool);  

        goto Exit1;  

    }  

  




 **See Also :**


**[FILEOBJECT](FILEOBJECT.md)**


**[NSFItemAppendObject](NSFItemAppendObject.md)**


**[NSFNoteAttachFile](NSFNoteAttachFile.md)**


**[OBJECT\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/00F300D5007E002085255EA00054AAD0)**



----------------------------------------------------------------------------------------------------------


 





