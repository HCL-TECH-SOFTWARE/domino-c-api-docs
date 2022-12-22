




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



**NSFDbFreeObject** **- Free the
space used by an object in a database file.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfobjec.h>**



STATUS
LNPUBLIC **NSFDbFreeObject(**  

      DBHANDLE  hDB,  

      DWORD  ObjectID**);**



**Description :**



This
function frees the space from a database file associated with an object.   

  

Use the Object ID to identify the object to free. The object ID (the RRV)
identifies the location of the object in the database file. Normally, you get
this object ID from the RRV member of the OBJECT\_DESCRIPTOR structure. The
OBJECT\_DESCRIPTOR structure is the value stored in an item of type TYPE\_OBJECT
in a note.   

  

Thus a Domino object consists of two parts: the object itself in the database,
and the object item in the note. This function frees the space reserved for the
object itself.  

  

Normally, you do not need to call NSFDbFreeObject explicitly when deleting an
item of type TYPE\_OBJECT. If the fDelete flag parameter to NSFItemAppendObject
was TRUE when the object item was appended to the note, then NSFItemDelete will
free the object automatically when the object item is deleted.


 


**Parameters :**



Input :  

hDB  -  handle to the open database where the object resides  

  

ObjectID  -  The object ID (the RRV) of the object to free. Get this ID from
the OBJECT\_DESCRIPTOR structure stored in an item of type TYPE\_OBJECT in a
note.  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Successfully freed object in database file.  

  

ERR\_xxx - Errors returned by lower level functions. Call OSLoadString to obtain
a string to display to the user.  

  

  




 **See Also :**


**[NSFDbAllocObject](NSFDbAllocObject.md)**


**[NSFDbGetObjectSize](NSFDbGetObjectSize.md)**


**[NSFDbReadObject](NSFDbReadObject.md)**


**[NSFDbReallocObject](NSFDbReallocObject.md)**


**[NSFDbWriteObject](NSFDbWriteObject.md)**


**[NSFItemAppendObject](NSFItemAppendObject.md)**


**[OBJECT\_DESCRIPTOR](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/004700B10077000185255EA0006A8D0C)**



----------------------------------------------------------------------------------------------------------


 





