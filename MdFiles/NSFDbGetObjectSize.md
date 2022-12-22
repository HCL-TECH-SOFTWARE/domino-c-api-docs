




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



**NSFDbGetObjectSize** **- Get the
size and class of an object in a database file.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfobjec.h>**



STATUS
LNPUBLIC **NSFDbGetObjectSize(**  

      DBHANDLE  hDB,  

      DWORD  ObjectID,  

      WORD  ObjectType,  

      DWORD far \*retSize,  

      WORD far \*retClass,  

      WORD far \*retPrivileges**);**



**Description :**



This
function returns the size (in bytes), the class, and the privileges mask of an
object in a Domino database file.    

  

Specify the object by its object ID. The object ID (the RRV) identifies the
location of the object in the database file. Get this object ID from the RRV
member of the OBJECT\_DESCRIPTOR structure. The OBJECT\_DESCRIPTOR structure
resides in an item of type TYPE\_OBJECT in a note.  

  

Use NSFDbGetObjectSize when updating an object to check that the size of the
object is large enough to store the updated object data. If the size of the
updated data exceeds the size of the object, call NSFDbReallocObject to
increase the amount of space reserved for the object in the database file.


 


**Parameters :**



Input :  

hDB  -  Handle to the open database containing the object.  

  

ObjectID  -  The object ID (the RRV) of the object. Get this from the RRV
member of an OBJECT\_DESCRIPTOR structure.  

  

ObjectType  -  The object type. OBJECT\_FILE for file attachments.  OBJECT\_FILTER\_LEFTTODO
for macro left-to-do Id table.  See Symbolic Value : Field OBJECT\_xxx for a
list of all possible values.   

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Successfully obtained object size and class.  

  

ERR\_xxx - Errors returned by lower level functions. Call OSLoadString to obtain
a string to display to the user.  

  

  

retSize  -  Optional;  if not NULL, receives the size, in bytes, of the
database object specified by the object ID.  

  

retClass  -  Optional;  if not NULL, receives the object class. Object classes
are the same as note classes (e.g. NOTE\_CLASS\_DOCUMENT). See Symbolic Value,
NOTE\_CLASS\_xxx for a list of all possible values.  

  

retPrivileges  -  Optional;  if not NULL, receives the privilege mask for this
object.  

  




 **Sample Usage :**


    /\* Get the size of
the existing $LeftToDo object. \*/  

  

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


**[NSFDbReadObject](NSFDbReadObject.md)**


**[NSFDbReallocObject](NSFDbReallocObject.md)**


**[NSFDbWriteObject](NSFDbWriteObject.md)**


**[NSFItemAppendObject](NSFItemAppendObject.md)**


**[OBJECT\_DESCRIPTOR](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/004700B10077000185255EA0006A8D0C)**



----------------------------------------------------------------------------------------------------------


 





