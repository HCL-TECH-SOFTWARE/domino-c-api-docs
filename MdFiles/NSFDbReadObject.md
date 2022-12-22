




<!--
 /\* Font Definitions \*/
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



**NSFDbReadObject** **- Read an
object into memory.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfobjec.h>**



STATUS
LNPUBLIC **NSFDbReadObject(**  

      DBHANDLE  hDB,  

      DWORD  ObjectID,  

      DWORD  Offset,  

      DWORD  Length,  

      DHANDLE far \*rethBuffer**);**



**Description :**



Read an
object from a database file into memory. This returns a handle specifying a
memory area where the object has been read. Free this memory after processing
it.  

  

Use the object ID (the RRV) to identify the object to read. Get this object ID
from the RRV member of an OBJECT\_DESCRIPTOR structure. The OBJECT\_DESCRIPTOR
structure resides in items of type TYPE\_OBJECT appended to notes.   

  

Domino and Notes use objects to store data that is not rendered on the screen
by the Notes editor. Examples include file attachments ($FILE fields), help
indexes, and macro left-to-do lists ($LeftToDo). Note that for file
attachments, NSFNoteExtractFile is simpler to use than NSFDbReadObject.


 


**Parameters :**



Input :  

hDB  -  Handle to the open database where the object resides  

  

ObjectID  -  Object ID (the RRV) identifying the object in the database. Get
this ID from the RRV member of the OBJECT\_DESCRIPTOR structure stored in items
of type TYPE\_OBJECT.  

  

Offset  -  Begin reading at this offset (in bytes) from the start of the
object. Specify 0 to start at the beginning of the object.  

  

Length  -  Number of bytes to read. Must not be zero.  Use MAXDWORD to read in
the number of bytes equal to the size of the object.   

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Successfully read object from database file to memory buffer.  

  

ERR\_OBJECT\_CANNOT\_BE\_ZERO - Length input parameter specified zero.  

  

ERR\_OBJECT\_TRUNCATED - Specified offset exceeds size of object, or length input
parameter exceeds object size minus offset.  

  

ERR\_xxx - Errors returned by lower level functions. Call OSLoadString to obtain
a string to display to the user.  

  

  

rethBuffer  -  Receives a handle to a memory area containing the object data
read from the file.  

  




 **Sample Usage :**


STATUS LNPUBLIC
ReadLeftToDoObject(


   DBHANDLE           
hDb,


   NOTEHANDLE         
hMacro,


   OBJECT\_DESCRIPTOR 
\*pObject,


   DHANDLE            
\*phLeftToDo,


   TIMEDATE          
\*ptdLeftToDoTime,


   WORD              
\*pwLeftToDoFlags )


{


   STATUS     
error;


   WORD       
wDataType;


   BLOCKID    
bidValue;


   DWORD      
dwValueLength;


   void      
\*ptable;


   OBJECT\_DESCRIPTOR 
tempObject;


   OBJECT\_DESCRIPTOR
\*tempPtr;


   


   error =
NSFItemInfo(hMacro, FILTER\_LEFTTODO\_ITEM, 


                      
sizeof(FILTER\_LEFTTODO\_ITEM)-1,


                      
NULL, &wDataType, &bidValue, &dwValueLength);


 


   if (
ERR(error) == ERR\_ITEM\_NOT\_FOUND )


   {


       return
(error);


   }


   else if
(error)


   {


       printf("Error:
unable get '%s' from Macro.\n",


          FILTER\_LEFTTODO\_ITEM);


       return(error);


   }


   if (wDataType
!= TYPE\_OBJECT)


   {


       printf
("Error: item '%s' not TYPE\_OBJECT.\n", FILTER\_LEFTTODO\_ITEM);


       return(error);


   }


        


   \*pObject =
\*((OBJECT\_DESCRIPTOR\*)(OSLockBlock(char,bidValue)+sizeof(WORD)));


 


   tempPtr =
pObject;


 


   ODSReadMemory(
&tempPtr, \_OBJECT\_DESCRIPTOR, &tempObject, 1 );


 


   if
(tempObject.ObjectType != OBJECT\_FILTER\_LEFTTODO)


   {                                                



       printf
("Error: object '%s' unknown type.\n",


          FILTER\_LEFTTODO\_ITEM);


       OSUnlockBlock(bidValue);


       return
(ERR\_RUNMACRO\_BADOBJECTTYPE);


   }


 


   error =
NSFDbReadObject(hDb, tempObject.RRV, 0, MAXDWORD, phLeftToDo);


   OSUnlockBlock(bidValue);


   if (error)


   {


      printf
("Error: unable to read object '%s'.\n", FILTER\_LEFTTODO\_ITEM);


       return
(error);


   }


 


   ptable =
OSLock(void, \*phLeftToDo);


   \*ptdLeftToDoTime
= IDTableTime(ptable);


   \*pwLeftToDoFlags
= IDTableFlags(ptable);


   OSUnlock(\*phLeftToDo); 
/\* unlock handle we are done with \*/


 


   return
NOERROR;


}


 **See Also :**


**[NSFItemAppendObject](NSFItemAppendObject.md)**


**[OBJECT\_DESCRIPTOR](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/004700B10077000185255EA0006A8D0C)**


**[NSFDbAllocObject](NSFDbAllocObject.md)**


**[NSFDbReallocObject](NSFDbReallocObject.md)**


**[NSFDbFreeObject](NSFDbFreeObject.md)**


**[NSFDbGetObjectSize](NSFDbGetObjectSize.md)**


**[NSFDbWriteObject](NSFDbWriteObject.md)**



----------------------------------------------------------------------------------------------------------


 





