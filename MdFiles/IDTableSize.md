




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



**IDTableSize** **- Returns
the size of the specified ID Table in bytes.**


**----------------------------------------------------------------------------------------------------------**



**#include <idtable.h>**



DWORD
LNPUBLIC **IDTableSize(**  

      DHANDLE  hTable**);**



**Description :**



This
function takes a HANDLE to an ID Table, then calculates and returns the size of
the entire ID Table in bytes.  Since an ID Table contains header information
and is compressed, the size returned cannot be computed based on the number of
IDs in the table.


 


**Parameters :**



Input :  

hTable  -  A HANDLE to the ID Table.  

  




Output :  

(routine)  -  Returns the size of the specified ID Table in bytes.  

  

  




 **Sample Usage :**


  

   printf("IDTableSize from function: %lu\n",  

           IDTableSize(idtable\_handle));  

  

  




 **See Also :**


**[IDTableFlags](IDTableFlags.md)**


**[IDTableTime](IDTableTime.md)**


**[IDTableSetFlags](IDTableSetFlags.md)**


**[IDTableSetTime](IDTableSetTime.md)**


**[IDTableSizeP](IDTableSizeP.md)**



----------------------------------------------------------------------------------------------------------


 





