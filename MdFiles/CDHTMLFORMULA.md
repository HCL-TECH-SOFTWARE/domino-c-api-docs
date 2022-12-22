




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




**Initial Release 4.6**



**Data Type : Rich Text; Composite
Data**



**CDHTMLFORMULA** **-** Formula for
attributes or alternate HTML text.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {


        WSIG    Header;                /\*
Tag and length \*/


        DWORD   dwFlags;                      /\*
Flags - denote what kind of formula this is \*/


        BYTE    cbLevel;                      /\*
\*/


        BYTE    cbReserved;                   /\*
Reserved for future use. \*/


        WORD    Reserved;                     /\*
Reserved for future use \*/


                                             /\*
The formula follows... \*/


}
CDHTMLFORMULA;


 


**Description :**



A
CDHTMLFORMULA record contains a formula used to generate either an attribute or
alternate HTML text for a Java applet.  The fields in this structure are:


 


Header             Identifies
this as a CDHTMLFORMULA record.


dwFlags           Flags
for this record;  see CDHTMLFORMULA\_FLAG\_xxx.


cbLevel 


cbReserved      Reserved; 
must be 0.


Reserved          Reserved; 
must be 0.


 


This record
is followed by the actual formula.


 **See Also :**


**[CDHTMLFORMULA\_FLAG\_xxx](CDHTMLFORMULA_FLAG_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





