




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




**Initial Release 6.5**



**Data Type : Composite Data; Rich
Text**



**CDEMBEDDEDCONTACTLIST** **-** Defines
properties of an embedded contact list.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct


        {


        WSIG
          Header; /\* Signature and length of this record. \*/


        DWORD          Flags;


        COLOR\_VALUE    SelectedBackground;


        COLOR\_VALUE    SelectedText;


        COLOR\_VALUE    ControlBackground;


                       


        DWORD          Spare[10];     /\*
Reserved for future use - must be zero \*/         


 


        }
CDEMBEDDEDCONTACTLIST;


 


**Description :**



This CD
record defines properties of an embedded contact list.  The fields in this
structure are:


  

Header - Signature and length of this record.


Flags - 


SelectedBackground
- Selected background color.  


SelectedText
-  


ControlBackground
- Control background.


Spare -
Reserved for future use - must be zero.  


 


Note that
rich text fields are items of type TYPE\_COMPOSITE.  Therefore, API programs
that run on non-Intel architecture platforms must perform host/canonical
conversion on CD record structures such as this when accessing rich text item
data in a note.


 **See Also :**


**[SIG\_CD\_xxx](SIG_CD_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





