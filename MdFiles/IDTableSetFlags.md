




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




 


**Function : ID Table**



**IDTableSetFlags** **- Sets the
Flag information of an ID Table.**


**----------------------------------------------------------------------------------------------------------**



**#include <idtable.h>**



void
LNPUBLIC **IDTableSetFlags(**  

      void far \*pIDTable,  

      WORD  Flags**);**



**Description :**



This
function sets the Flag information of an ID Table.  See the IDTABLE\_xxx symbols
for further information.


 


**Parameters :**



Input :  

pIDTable  -  A pointer to an ID Table.  

  

Flags  -  A WORD containing the IDTABLE\_xxx flags you'd like to have associated
with the ID Table.  

  




Output :  

(routine)  -  None.  

  

  




 **Sample Usage :**


  

   if (IDTableFlags(idtable\_ptr) & IDTABLE\_MODIFIED)  

  

       /\* Well we didn't,so NSFDbGetModifiedNoteTable() must have \*/  

       /\* Will clear modified flag for our own puposes            \*/  

  

       IDTableSetFlags(idtable\_ptr, 0);  

  




 **See Also :**


**[IDTableFlags](IDTableFlags.md)**


**[IDTableSetTime](IDTableSetTime.md)**


**[IDTableSize](IDTableSize.md)**


**[IDTableTime](IDTableTime.md)**


**[IDTABLE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255BCF005DFB88)**



----------------------------------------------------------------------------------------------------------


 





