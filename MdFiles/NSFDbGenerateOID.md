




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



**NSFDbGenerateOID** **- Create
new Originator ID for note in database.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbGenerateOID(**  

      DBHANDLE  hDB,  

      OID far \*retOID**);**



**Description :**



This
function generates a new Originator ID (OID) used to uniquely identify a note. 
Use this function when you already have a note open and wish to create a
totally new note with the same items as the open note.  This function is
commonly used after NSFNoteCopy, because the copy created by NSFNoteCopy has
the same OID as the source note.  

  

You do not need NSFDbGenerateOID when creating a new note from scratch using
NSFNoteCreate, because NSFNoteCreate performs this function for you.  

  

If the database resides on a remote Lotus Domino Server, the current user must
to have the appropriate level of access to carry out this operation.


 


**Parameters :**



Input :  

hDB  -  A handle to a Domino database.    

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully generated a new Originator ID.  

ERR\_NTCREATE\_LICENSE - Cannot create a document without a valid user license.  

  

  

retOID  -  The address of an OID structure in which the new OID will be
returned.  

  




 **Sample Usage :**


  

   /\* Update Note Info as if a delete & an add had taken place      \*/  

   

  if (error\_status = NSFDbGenerateOID(db\_handle\_dst, &new\_oid))  

       goto Exit;  

   NSFNoteSetInfo(note\_handle, \_NOTE\_OID, &new\_oid);  

  




 **See Also :**


**[NSFNoteGetInfo](NSFNoteGetInfo.md)**


**[NSFNoteSetInfo](NSFNoteSetInfo.md)**


**[NSFNoteUpdate](NSFNoteUpdate.md)**


**[\_NOTE\_xxx](_NOTE_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





