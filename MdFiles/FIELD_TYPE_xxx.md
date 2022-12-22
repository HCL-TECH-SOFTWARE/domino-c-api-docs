




<!--
 /\* Font Definitions \*/
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




 


**Symbolic Value : Add-In DLL**



**FIELD\_TYPE\_xxx** **-** Editor field
types.


**----------------------------------------------------------------------------------------------------------**



**#include <editdflt.h>**


 **Symbolic Values :**      FIELD\_TYPE\_ERROR          -  Field type cannot be
determined.  

  

      FIELD\_TYPE\_NUMBER        -  Number field.  

  

      FIELD\_TYPE\_TIME   -  Time field.  

  

      FIELD\_TYPE\_RICH\_TEXT   -  Rich text field.  

  

      FIELD\_TYPE\_AUTHORS      -  Authors field.  

  

      FIELD\_TYPE\_READERS      -  Readers field.  

  

      FIELD\_TYPE\_NAMES          -  Names field.  

  

      FIELD\_TYPE\_KEYWORDS   -  Keyword field.  

  

      FIELD\_TYPE\_TEXT             -  Plain text field.  

  

      FIELD\_TYPE\_SECTION       -  Section field.  

  

      FIELD\_TYPE\_PASSWORD   -  Password field.  

  

      FIELD\_TYPE\_FORMULA      -  Formula field.  

  

      FIELD\_TYPE\_TIMEZONE     -  Time zone field  

  

      FIELD\_TYPE\_COLORCTL    -  Color control field  

  




**Description :**



This information
is passed to the NAMM\_COMMAND message processing routine in an Add-In DLL via
the CaretFieldType member of the EDITIXDATA structure.  It identifies the field
type of the field containing the cursor when the Add-In's menu item was chosen.


 **See Also :**


**[EDITIXDATA](EDITIXDATA.md)**



----------------------------------------------------------------------------------------------------------


 





