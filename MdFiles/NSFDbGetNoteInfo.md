




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



**NSFDbGetNoteInfo** **- Get 
information from a note's on-disk header.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbGetNoteInfo(**  

      DBHANDLE  hDb,  

      NOTEID  NoteID,  

      OID far \*retNoteOID,  

      TIMEDATE far \*retModified,  

      WORD far \*retNoteClass**);**



**Description :**



This
function takes a database handle and note ID.  It returns the note's the
Originator ID (OID) structure, the time and date the note was last modified,
and the NOTE\_CLASS\_xxx.  It is the database level equivalent of three calls to
NSFNoteGetInfo(), but requires a disk I/O or network I/O to obtain the
information (and thus, it is fairly expensive to use).


 


**Parameters :**



Input :  

hDb  -  A handle to an open Domino database.  

  

NoteID  -  The NOTEID of the note whose particulars you wish to retrieve.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully retrieved the note information.  

  

ERR\_NOTE\_DELETED - Document has been deleted.  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

retNoteOID  -  Returns the populated ORIGINATORID (OID) structure containing
the database creation time/date, note creation time/date, note sequence number,
and the sequence time/date (when added to database).   

  

retModified  -  Returns the populated TIMEDATE structure containing the note's
last modified time and date normalized to Greenwich Mean Time (GMT).    

  

retNoteClass  -  Returns  pointer to NOTE\_CLASS\_xxx in a WORD, value indicates
the type of note.    

  




 **Sample Usage :**


    

   /\* Find some SPECIAL notes: Policy and then designer's Help \*/  

     

   if (error\_status = NSFDbGetSpecialNoteID(db\_handle\_src,  

                          SPECIAL\_ID\_NOTE | NOTE\_CLASS\_INFO,  

                          &policy\_nid\_src))  

   {  

       if (ERR(error\_status) == ERR\_SPECIAL\_ID)  

           printf("\n%s has no Policy Note\n", src\_name);  

       else  

           goto Exit;  

   }  

   else  

   {  

       if (error\_status = NSFDbGetNoteInfo(db\_handle\_src,  

                                           policy\_nid\_src,  

                                           &policy\_oid\_src,  

                                           &policy\_lastmod\_td,  

                                           &policy\_noteclass))  

           goto Exit;  

       printf("Policy Note ID = %08lX\n", policy\_oid\_src.Note);  

   }  

  




 **See Also :**


**[NSFDbOpen](NSFDbOpen.md)**


**[NSFDbOpenExtended](NSFDbOpenExtended.md)**


**[NSFDbGetSpecialNoteID](NSFDbGetSpecialNoteID.md)**


**[NSFDbGetNoteInfoByUNID](NSFDbGetNoteInfoByUNID.md)**


**[NSFNoteGetInfo](NSFNoteGetInfo.md)**



----------------------------------------------------------------------------------------------------------


 





