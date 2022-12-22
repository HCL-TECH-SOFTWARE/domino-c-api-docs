




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




**Initial Release 7.0.2**



**Function : MIME**



**NSFNoteHasRFC822Text** **- Check to
see if the given note has any items of TYPE\_RFC822\_TEXT.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



BOOL
LNPUBLIC **NSFNoteHasRFC822Text(**  

      NOTEHANDLE  hNote**);**



**Description :**



The function
NSFNoteHasRFC822Text returns TRUE if the given note contains any
TYPE\_RFC822\_TEXT items.


 


**Parameters :**



Input :  

hNote  -  a handle to an open note.  

  




Output :  

(routine)  -  TRUE if the given note has any TYPE\_RFC822\_TEXT items, FALSE
otherwise.  

  

  

  




 **Sample Usage :**


    BOOL
bHasRFC822Text;


 


 


bHasRFC822Text =
NSFNoteHasRFC822Text(hNote);


 


 **See Also :**


**[NSFNoteHasComposite](NSFNoteHasComposite.md)**


**[NSFNoteHasMIME](NSFNoteHasMIME.md)**


**[NSFNoteHasMIMEPart](NSFNoteHasMIMEPart.md)**


**[NSFNoteHasObjects](NSFNoteHasObjects.md)**



----------------------------------------------------------------------------------------------------------


 





