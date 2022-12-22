




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




 


**Data Type : Number**



**NFMT** **-** Formats for
character text number string conversions.


**----------------------------------------------------------------------------------------------------------**



**#include
<misc.h>**



**Definition :**



typedef struct {  

    BYTE Digits;                                 /\* Number of decimal digits \*/  

    BYTE Format;                                 /\* Display Format \*/  

    BYTE Attributes;                             /\* Display Attributes \*/  

    BYTE Unused;  

} NFMT;  

  




 


**Description :**



This
structure holds the format for character text number strings. You set up this
structure based on the number format you want to use. Definitions for the
various fields of this structure are found in NFMT\_xxx and NATTR\_xxx.


 **Sample Usage :**


  

/\*  

 \*  Set up Number format  

 \*/    

  

NFMT NumberFormat;    

  

NumberFormat.Digits     = 6;  

NumberFormat.Format     = NFMT\_GENERAL;  

NumberFormat.Attributes = NATTR\_PUNCTUATED;  

NumberFormat.Unused     = 0;  

  




 **See Also :**


**[NATTR\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/B646EF784546BE0385256678005EF788)**


**[NFMT\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/00DE002900D0004A85255EAC006644F7)**



----------------------------------------------------------------------------------------------------------


 





