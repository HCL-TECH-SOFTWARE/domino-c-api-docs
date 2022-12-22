




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




 


**Data Type : Views**



**VIEW\_FORMAT\_HEADER** **-** Header
structure used in VIEW\_TABLE\_FORMAT


**----------------------------------------------------------------------------------------------------------**



**#include
<viewfmt.h>**



**Definition :**



typedef struct {  

   BYTE Version;   /\* Version number \*/  

   BYTE ViewStyle; /\* View Style - Table,Calendar \*/  

} VIEW\_FORMAT\_HEADER;


 


**Description :**



This defines
the structure of the header member of the VIEW\_TABLE\_FORMAT structure.  The
VIEW\_TABLE\_FORMAT structure is part of a $VIEWFORMAT item (also known as a
"View Table Format" item), which is an item in all view notes.


 **Sample Usage :**


  

    VIEW\_TABLE\_FORMAT  ViewTableFormat;  

  

/\*  

 \* Initialize the VIEW\_TABLE\_FORMAT structure.  

 \*/  

  

    ViewTableFormat.Header.Version = VIEW\_FORMAT\_VERSION;  

    ViewTableFormat.Header.ViewStyle = VIEW\_STYLE\_TABLE;


 **See Also :**


**[VIEW\_TABLE\_FORMAT](VIEW_TABLE_FORMAT.md)**



----------------------------------------------------------------------------------------------------------


 





