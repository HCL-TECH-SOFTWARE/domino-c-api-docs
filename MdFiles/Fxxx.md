




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




 


**Symbolic Value : Form**



**Fxxx** **-** CDFIELD -
Flags


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      FREADWRITERS     -  Field contains read/writers  

  

      FEDITABLE              -  Field is editable, not read only  

  

      FNAMES     -  Field contains distinguished names  

  

      FSTOREDV              -  Store Default Value, even if not spec'ed by user  

  

      FREADERS              -  Field contains document readers  

  

      FSECTION   -  Field contains a section  

  

      FSPARE3     -  Can be assumed to be clear in memory (V3 & later)  

  

      FV3FAB        -  IF CLEAR, CLEAR AS ABOVE  

  

      FCOMPUTED           -  Field is a computed field  

  

      FKEYWORDS           -  Field is a keywords field  

  

      FPROTECTED         -  Field is protected  

  

      FREFERENCE          -  Field name is simply a reference to a shared field
note  

  

      FSIGN          -  Sign this field during mail signing, or when the field
is saved within a section.  

  

      FSEAL          -  Enable encryption for this field.  

  

      FKEYWORDS\_UI\_STANDARD         -  Standard UI  

  

      FKEYWORDS\_UI\_CHECKBOX         -  Checkbox UI  

  

      FKEYWORDS\_UI\_RADIOBUTTON   -  Radiobutton UI  

  

      FKEYWORDS\_UI\_ALLOW\_NEW      -  Allow doc editor to add new values.  

  




**Description :**



Defines the
flags that may be set in the Flags member of the CDFIELD data structure.


 **See Also :**


**[CDFIELD](CDFIELD.md)**



----------------------------------------------------------------------------------------------------------


 





