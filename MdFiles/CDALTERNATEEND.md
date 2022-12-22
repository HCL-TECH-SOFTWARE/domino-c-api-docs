




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




**Initial Release 4.5**



**Data Type : Composite Data; Rich
Text**



**CDALTERNATEEND** **-** End of
alternate display records.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   BSIG  Header; /\* Signature and length of this record \*/  

   DWORD Flags;  /\* Unused; must be 0 \*/  

} CDALTERNATEEND;


 


**Description :**



This record
marks the end of a sequence of CD records comprising the alternate
representation of an active object.  For more information, please see the entry
for CDALTERNATEBEGIN.  The fields in this record are:


 


Header                         Identifies
this as a CDALTERNATEEND record


Flags                            Currently
unused;  must be 0


 


 **See Also :**


**[CDALTERNATEBEGIN](CDALTERNATEBEGIN.md)**



----------------------------------------------------------------------------------------------------------


 





