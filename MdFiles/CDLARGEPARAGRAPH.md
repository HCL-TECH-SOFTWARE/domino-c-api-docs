




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



**CDLARGEPARAGRAPH** **-** Contains
large paragraph information for Notes/Domino 6.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {


        WSIG
Header;           /\* Signature and length of this record \*/


        WORD
Version;


        WORD
Flags;            


#define
CDLARGEPARAGRAPH\_BEGIN        0x0001


#define
CDLARGEPARAGRAPH\_END  0x0002


        DWORD
Spare[2];


}
CDLARGEPARAGRAPH;


 


**Description :**



The 64K
limit on paragraphs has been removed in Notes/Domino 6.  To ensure backward
compatibility, "large" paragraphs are broken into smaller paragraphs
which are bracketed by a CDLARGEPARAGRAPH record with its Flags member set to
CDLARGEPARAGRAPH\_BEGIN and a CDLARGEPARAGRAPH record with its Flags member set
to CDLARGEPARAGRAPH\_END. 


 


R5 will
ignore the two CDLARGEPARAGRAPH records and load the small paragraphs.
Notes/Domino 6 will combine the small paragraphs between these two CD records
along with the paragraph which precedes them into one single paragraph at
run-time and split them again when the document is saved.


  

The fields in this structure are:  

  




    Header -
Signature and length of this record.


    


    Version
-  See LARGEPARAGRAPH\_xxx.


 


    Flags - 
See CDLARGEPARAGRAPH\_xxx.


 


    Spare -
Future use.


 


Note that
CDLARGEPARAGRAPH records reside in items of type TYPE\_COMPOSITE. Therefore, API
programs that run on non-Intel architecture platforms must perform
host/canonical conversion on structures of this type when accessing these
records in an item in a note.


 **See Also :**


**[CDLARGEPARAGRAPH\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/BD7EF9A1F6F2C82085256BF200501180)**


**[LARGEPARAGRAPH\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0F4B03EACC93F74C85256C2A006B32C9)**



----------------------------------------------------------------------------------------------------------


 





