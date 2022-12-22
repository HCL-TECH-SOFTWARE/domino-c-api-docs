




<!--
 /\* Font Definitions \*/
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




**Initial Release 4.6.1**



**Symbolic Value : Form**



**ACTION\_xxx (type)** **-** CDACTION
Type.


**----------------------------------------------------------------------------------------------------------**



**#include <actprop.h>**


 **Symbolic Values :**      ACTION\_RUN\_FORMULA    -  Formula ActionType.  

  

      ACTION\_RUN\_SCRIPT        -  Script Action Type.  

  

      ACTION\_RUN\_AGENT         -  Agent Action Type.  

  

      ACTION\_OLDSYS\_COMMAND         -  System Command Action Type.  

  

      ACTION\_SYS\_COMMAND   -  System Command Action Type.  

  

      ACTION\_PLACEHOLDER     -  Place holder for Action Type.  

  

      ACTION\_RUN\_JAVASCRIPT            -  Java Script Action Type.  

  




**Description :**



The CDACTION
structure contains an action Type member of one of the above.


 


      
ACTION\_RUN\_JAVASCRIPT is an V5 Action Type, and the CD record of this type
should be defined in the rich-text item "$V5ACTIONS", not the
"$ACTIONS".


 **See Also :**


**[CDACTION](CDACTION.md)**



----------------------------------------------------------------------------------------------------------


 





