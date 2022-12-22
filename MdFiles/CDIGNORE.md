




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




**Initial Release 6**



**Data Type : Composite Data; Rich
Text**



**CDIGNORE** **-** Used to
ignore a block of CD records for a particular version of Notes.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct


        {


        BSIG    Header;


        WORD    wNotesVersion; /\*
Version of Notes... See below.  \*/


        DWORD   dwFlags;               /\*
See FLAG\_CDIGNORE\_ below. \*/


        DWORD   dwUnused[6];   /\*
Reserved for future use. Should be zeroed out. \*/


        }
CDIGNORE;


 


**Description :**



Used to
ignore a block of CD records for a particular version of Notes.  The block
starts with a CDIGNORE with its dwFlags member set to FLAG\_CDIGNORE\_BEGIN and
ends with another CDIGNORE record with its dwFlags member set to
FLAG\_CDIGNORE\_END.  The CD records in between a CDIGNORE "begin" and
a CDINGORE "end" should be ignored when the wNotesVersion is less
than or equal to CDIGNORE\_NOTES\_VERSION\_CURRENT. CDIGNORE records may be
nested. 


 


The
fields in this structure are:  

  




Header -
Signature and length of this record.


    


wNotesVersion
- See CDIGNORE\_NOTES\_VERSION\_xxx.


 


dwFlags -  
See FLAG\_CDIGNORE\_xxx.


 


dwUnused -
Reserved for future use. Should be zeroed out.


 


Note
that CDIGNORE records reside in items of type TYPE\_COMPOSITE. Therefore, API
programs that run on non-Intel architecture platforms must perform
host/canonical conversion on structures of this type when accessing these
records in an item in a note.


 **See Also :**


**[ACTION\_IGNORE\_SYSTEM\_ACTIONS\_VERSION1](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/B67320B7475D6DB885256C2A00686364)**


**[CDIGNORE\_NOTES\_VERSION\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/2D178BA0AE8448A085256C2A006C9A9B)**


**[FLAG\_CDIGNORE\_xxx](FLAG_CDIGNORE_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





