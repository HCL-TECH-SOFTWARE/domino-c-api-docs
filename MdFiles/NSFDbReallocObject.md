




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



**NSFDbReallocObject** **-
Re-allocate an object to change its size.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfobjec.h>**



STATUS
LNPUBLIC **NSFDbReallocObject(**  

      DBHANDLE  hDB,  

      DWORD  ObjectID,  

      DWORD  NewSize**);**



**Description :**



This
function reallocates an object in the database file to accommodate a different
size. The object ID (the RRV) remains the same even after the object is
reallocated.  

  

Use this function when updating an object in a database if the updated size of
the object is greater than the original object. Use NSFDbGetObjectSize to
obtain the size of an object initially.  

  

Domino and Notes use objects and object items to store data that is not
rendered on the screen by the Notes editor. Examples include file attachments
($FILE fields), help indexes, and macro left-to-do lists ($LeftToDo). Note that
for file attachments, NSFNoteAttachFile and NSFNoteDetatchFile are simpler to
use than NSFDbReadObject and NSFDbWriteObject.


 


**Parameters :**



Input :  

hDB  -  handle to the open database in which the object resides  

  

ObjectID  -  The object ID (the RRV) that identifies the location of the object
in the database file. Obtain this ID originally from NSFDbAllocateObject. This
ID is stored in the RRV member of the OBJECT\_DESCRIPTOR structure, which is stored
in note fields of type TYPE\_OBJECT.  

  

NewSize  -  The new size, in bytes, of the object. On successfull return, the
object specified by ObjectID has at least this much space.  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Successfully re-allocated object to requested size.  

  

ERR\_xxx - Errors returned by lower level functions. Call OSLoadString to obtain
a string to display to the user.  

  

  




 **Sample Usage :**


  

    DBHANDLE    hDb;  

    OBJECT\_DESCRIPTOR   objLeftToDo;  

    DWORD       dwNeededSize, dwExistingSize;  

    WORD        wClass, wPrivs;  

  

    /\* Get the size of the existing $LeftToDo object. \*/  

  

    if (error = NSFDbGetObjectSize(hDb,   

                        objLeftToDo.RRV,   

                        objLeftToDo.ObjectType,  

                        &dwExistingSize, &wClass, &wPrivs))  

    {  

        printf ("Error: unable to get size of object '%s' in
macro.\n",  

                        FILTER\_LEFTTODO\_ITEM);  

        goto Exit2;  

    }  

  

    /\* Reallocate the existing object if necessary. \*/  

  

    if (dwExistingSize < dwNeededSize)  

    {  

        /\* realloc 1K more than needed so won't have to realloc as often \*/  

        if (error = NSFDbReallocObject(hMacro,  

                                    objLeftToDo.RRV, dwNeededSize+1024))  

        {  

            printf ("Error: unable to re-allocate '%s' to %ld
bytes.\n",  

                        FILTER\_LEFTTODO\_ITEM, dwNeededSize);  

            goto Exit2;  

        }  

    }  

  

    /\*  Write the object \*/  

    if (error = NSFDbWriteObject(hDb, objLeftToDo.RRV,   

                        hLeftToDo, 0,  

                        dwNeededSize))  

    {  

        printf ("Error: unable to write '%s' object to macro
note.\n",  

                                FILTER\_LEFTTODO\_ITEM);  

    }  

  




 **See Also :**


**[NSFDbAllocObject](NSFDbAllocObject.md)**


**[NSFDbFreeObject](NSFDbFreeObject.md)**


**[NSFDbGetObjectSize](NSFDbGetObjectSize.md)**


**[NSFDbReadObject](NSFDbReadObject.md)**


**[NSFDbWriteObject](NSFDbWriteObject.md)**


**[NSFItemAppendObject](NSFItemAppendObject.md)**


**[OBJECT\_DESCRIPTOR](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/004700B10077000185255EA0006A8D0C)**



----------------------------------------------------------------------------------------------------------


 





