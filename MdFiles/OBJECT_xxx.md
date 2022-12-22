




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




 


**Symbolic Value : Field**



**OBJECT\_xxx** **-** Object types
used in OBJECT\_DESCRIPTOR structure


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdata.h>**


 **Symbolic Values :**      OBJECT\_NO\_COPY             -  A flag that may be bitwise
OR-ed with the object type value. Prevents object from being copied when note
is copied.  

  

      OBJECT\_PRESERVE           -  A flag that may be bitwise OR-ed with the
object type to prevent Domino or Notes from deleting the object when a note
that refers to the object is deleted.  

  

      OBJECT\_PUBLIC     -  Public access object being allocated.  

  

      OBJECT\_FILE          -  File Attachment.  

  

      OBJECT\_FILTER\_LEFTTODO         -  The $LeftToDo object associated with a
macro: has an ID table of docs not yet processed by the macro.  

  

      OBJECT\_ASSIST\_RUNDATA           -  Assistant run data object.  

  

      OBJECT\_UNKNOWN           -  Unknown object type. Specify in
NSFDbGetObjectSize() if you do not know the object type.  

  




**Description :**



These values
reside in the ObjectType member of the OBJECT\_DESCRIPTOR structure. They are
also specified in the ObjectType argument to the function NSFDbGetObjectSize().
The object type characterizes what sort of information resides in an object.  

  

All items of type TYPE\_OBJECT have an OBJECT\_DESCRIPTOR structure. The
ObjectType member of the OBJECT\_DESCRIPTOR structure differentiates between
different types of objects.   

  

File attachments are items of type TYPE\_OBJECT with field name $FILE and object
type OBJECT\_FILE.   

  

Macro left-to-do lists are items of type TYPE\_OBJECT with field name $LeftToDo
and object type OBJECT\_FILTER\_LEFTTODO.   

  

For either of the above object types, you may specify OBJECT\_UNKNOWN as the
ObjectType argument to NSFDbGetObjectSize() and obtain the correct result.  

  

OBJECT\_NO\_COPY and OBJECT\_PRESERVE flags may be bitwise OR-ed with certain
object types. These flags affect  how Domino or Notes handles objects when
copying or updating a note containing the object. Normally these flags are not
used with either of the above object types.


 **Sample Usage :**


  

    DWORD       dwObjectID;  

    OBJECT\_DESCRIPTOR   objLeftToDo;  

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

        printf ("Error: unable to allocate %ld bytes for LeftToDo item.\n",  

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


**[OBJECT\_DESCRIPTOR](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/004700B10077000185255EA0006A8D0C)**


**[FILEOBJECT](FILEOBJECT.md)**


**[NSFNoteAttachFile](NSFNoteAttachFile.md)**


**[NSFItemAppendObject](NSFItemAppendObject.md)**


**[NSFDbGetObjectSize](NSFDbGetObjectSize.md)**



----------------------------------------------------------------------------------------------------------


 





