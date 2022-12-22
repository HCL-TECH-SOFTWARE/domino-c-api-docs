




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



**HEAD\_DESC** **-** Header/Footer
Data Structure Passed to Import/Export Modules


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   BYTE    FontPitchAndFamily;    /\* Font pitch and family \*/  

   char    FontName[MAXFACESIZE]; /\* Font name \*/  

   FONTID  Font;                         /\* Font ID \*/  

   WORD    HeadLength;            /\* string length not including '\0' \*/  

    /\* Header string follows \*/  

} HEAD\_DESC;


 


**Description :**



This data
structure is passed to Import/Export modules to describe the header or footer
for a document.  

  

        FontPitchAndFamily        Pitch and font family of font used to display
the data  

        FontName                           Name of font to use  

        Font                                       ID of font to use  

        HeadLength                       Total string length of header or
footer  

  




 **See Also :**


**[EDITEXPORTDATA](EDITEXPORTDATA.md)**


**[HEAD\_DESC\_BUFFER](HEAD_DESC_BUFFER.md)**



----------------------------------------------------------------------------------------------------------


 





