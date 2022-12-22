




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




 


**Symbolic Value : Limits**



**DESIGN\_xxx\_MAX** **-** Maximum
lengths of various design note elements.


**----------------------------------------------------------------------------------------------------------**



**#include <names.h>**


 **Symbolic Values :**      DESIGN\_LEVEL\_MAX          -  Maximum length per level of the
name of a design element. The names of some design elements can cascade one
level (and therefore be longer), while the names of other design elements
cannot cascade.  

  

      DESIGN\_NAME\_MAX           -  The maximum length for the name of a design
note. Will always be the largest of DESIGN\_FORM\_MAX, DESIGN\_VIEW\_MAX, and DESIGN\_MACRO\_MAX.  

  

      DESIGN\_FORM\_MAX           -  The maximum length for the name of a form
note. Can cascade one level.  

  

      DESIGN\_VIEW\_MAX            -  The maximum length for the name of a view
note. Can cascade one level.  

  

      DESIGN\_MACRO\_MAX        -  The maximum length for the name of a macro
note. Can cascade one level.  

  

      DESIGN\_FIELD\_MAX           -  The maximum length for the name of a field.
Cannot cascade.  

  

      DESIGN\_COMMENT\_MAX   -  The maximum length of a design note's comment
element.  

  

      DESIGN\_ALL\_NAMES\_MAX             -  The maximum cumulative length of all
names of a design note, including synonyms.  

  

      DESIGN\_FOLDER\_MAX       -  The maximum length for the name of a folder
note. Can cascade one level.  

  

      DESIGN\_FOLDER\_MAX\_NAME        -  Maximum length per level of the name of
a folder.  

  

      DESIGN\_FLAGS\_MAX          -  The maximum length of the DESIGN\_FLAGS
($Flags) item in a design note.  

  




**Description :**



Maximum
lengths of various design note elements.


 




----------------------------------------------------------------------------------------------------------


 





