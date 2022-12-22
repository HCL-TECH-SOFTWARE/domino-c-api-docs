




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




 


**Function : Note**



**NSFNoteGetInfo** **- Gets
specified value from in-memory note header.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



void
LNPUBLIC **NSFNoteGetInfo(**  

      NOTEHANDLE  note\_handle,  

      WORD  note\_member,  

      void far \*value\_ptr**);**



**Description :**



This function
gets a specified value from an in-memory note header.  It takes a handle to an
open note,  a note member ID identifying the information you wish to obtain,
and the address of a variable where the requested data will be returned. 


 


**Parameters :**



Input :  

note\_handle  -  The handle of an open note.  

  

note\_member  -  A WORD containing the note member ID (see \_NOTE\_xxx) for the
note header value you wish to get.  

  




Output :  

(routine)  -  None.  

  

  

value\_ptr  -  The address of an existing variable or Domino memory object in
which the requested note header data will be returned.  

  




 **Sample Usage :**


  

   /\* Since NID only exists if Note exists on disk, Update, Get,  \*/     

   /\* and store the resulting NID                                 \*/  

   if (error\_status = NSFNoteUpdate(note1\_handle, UPDATE\_FORCE))  

       goto Exit;  

   NSFNoteGetInfo(note1\_handle, \_NOTE\_ID, &note1\_id);  

  




 **See Also :**


**[NSFDbGenerateOID](NSFDbGenerateOID.md)**


**[NSFNoteClose](NSFNoteClose.md)**


**[NSFNoteOpen](NSFNoteOpen.md)**


**[NSFNoteSetInfo](NSFNoteSetInfo.md)**


**[NSFNoteUpdate](NSFNoteUpdate.md)**


**[\_NOTE\_xxx](_NOTE_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





