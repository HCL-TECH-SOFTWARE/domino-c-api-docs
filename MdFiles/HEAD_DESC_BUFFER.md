




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




 


**Data Type : Rich Text**



**HEAD\_DESC\_BUFFER** **-** Header/Footer
Buffer


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   HEAD\_DESC Desc;              /\* Header/footer description \*/  

   char String[MAXHEADERSTRING];  /\* Buffer for text - 


                                   
Must be '\0' terminated \*/  

} HEAD\_DESC\_BUFFER;


 


**Description :**



This data
structure is passed to Import/Export modules to describe the header or footer
for a document.  This structure consists of a HEAD\_DESC header followed by an
array of type "char" for the header or footer string.  

  

        Desc            HEAD\_DESC structure describing the header or footer  

        String            Text for the header or footer


 **See Also :**


**[EDITEXPORTDATA](EDITEXPORTDATA.md)**


**[HEAD\_DESC](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/6E9151037CE84CE5852560510052CFF9)**



----------------------------------------------------------------------------------------------------------


 





