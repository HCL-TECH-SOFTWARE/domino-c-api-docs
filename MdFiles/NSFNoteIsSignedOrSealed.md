




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




 


**Function : Note**



**NSFNoteIsSignedOrSealed** **-
Determines if note is signed and/or sealed.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



BOOL
LNPUBLIC **NSFNoteIsSignedOrSealed(**  

      NOTEHANDLE  note\_handle,  

      BOOL far \*signed\_flag\_ptr,  

      BOOL far \*sealed\_flag\_ptr**);**



**Description :**



This
function determines if an in-memory note is signed and/or sealed (encrypted).    

  

A signed Note contains an additional item, which is generated using the Note
Author's private encryption key from his or her USER ID.  This does not prevent
you from accessing any of the note's Items or header information, except of
course, the ITEM\_NAME\_NOTE\_SIGNATURE item itself.   

  

A sealed Note contains at least two additional items,  ITEM\_NAME\_NOTE\_SEAL and
ITEM\_NAME\_NOTE\_SEALDATA.  You may use NSFNoteDecrypt to decrypt a sealed note.


 


This
functions works for both notes and native MIME messages.  However, only the
outer envelope of the native MIME message is checked.  This means that SMIME
signed/sealed messages which are nested within the native MIME message will not
be detected.


 


**Parameters :**



Input :  

note\_handle  -  The handle of an open note.  

  




Output :  

(routine)  -  Returned from this call-  

  

TRUE - Note was either signed or sealed.  

FALSE - Note was neither signed nor sealed.  

  

  

signed\_flag\_ptr  -  The addres of a BOOL in which the Signed state of the Note
is returned.  TRUE if Signed and False if not Signed.  

  

sealed\_flag\_ptr  -  The address of a BOOL in which the Sealed state of the Note
is returned.  TRUE if Sealed and False if not Sealed.  

  




 **See Also :**


**[NSFNoteOpen](NSFNoteOpen.md)**


**[NSFNoteClose](NSFNoteClose.md)**


**[NSFNoteDecrypt](NSFNoteDecrypt.md)**



----------------------------------------------------------------------------------------------------------


 





