




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




 


**Function : Note; Note Open/Note
Update Hook Drivers**



**NSFNoteOpenByUNIDExtended** **- Return a
Notes document handle using the Universal Note ID.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS **NSFNoteOpenByUNIDExtended(**  

      DBHANDLE  hDB,  

      UNID  pUNID,  

      DWORD  flags,  

      NOTEHANDLE  rethNote**);**



**Description :**




Read
the Universal Note ID into memory and return a handle to the in-memory copy.
DWORD options are described in the entry OPEN\_xxx. 


 


Use
NSFNoteClose to close the note handle and deallocate the memory associated with
it.


 


**Parameters :**



Input :  

hDB  -  The handle of the open database that contains the note.  

  

pUNID  -  The Universal Note ID.  

  

flags  -  Flags that control the manner in which the note is opened. This, in
turn, controls what information about the note is available to you and how it is
structured. The flags are defined in OPEN\_xxx (note) and may be or'ed together
to combine functionality.  

  




Output :  

(routine)  -  Returns status from the call, either success or an error.  

  

  

rethNote  -  The address in which the handle of the opened note is returned.  

  




 **Sample Usage :**


      NOTEHANDLE
hNote = NULLHANDLE;


            DWORD
Flags = OPEN\_CANONICAL | OPEN\_UNLINKED | OPEN\_RAW\_MIME;


 


            /\*
Where myUNID is a variable of type UNID. \*/


            if(status
= NSFNoteOpenByUNIDExtended(hDb, myUNID, Flags, &hNote))


                        printf("UNID
not found or Note is invalid, error = %e", status);


 **See Also :**




----------------------------------------------------------------------------------------------------------


 





