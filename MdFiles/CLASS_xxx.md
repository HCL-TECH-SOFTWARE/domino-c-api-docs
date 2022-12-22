




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




 


**Symbolic Value : Field**



**CLASS\_xxx** **-** Item Class
definitions.


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdata.h>**


 **Symbolic Values :**      CLASS\_NOCOMPUTE          -  Non-computable data types. See
nsfdata.h for a full list of the data types that are in this class. These data
types include:  

 TYPE\_INVALID\_OR\_UNKNOWN  

 TYPE\_COMPOSITE  

TYPE\_COLLATION  

TYPE\_OBJECT  

TYPE\_NOTEREF\_LIST  

TYPE\_VIEW\_FORMAT  

TYPE\_ICON   

TYPE\_NOTELINK\_LIST  

TYPE\_SIGNATURE  

TYPE\_SEAL   

TYPE\_SEALDATA  

TYPE\_SEAL\_LIST  

TYPE\_HIGHLIGHTS  

TYPE\_WORKSHEET\_DATA  

TYPE\_USERDATA  

TYPE\_QUERY  

TYPE\_ACTION  

TYPE\_ASSISTANT\_INFO  

TYPE\_VIEWMAP\_DATASET  

TYPE\_VIEWMAP\_LAYOUT  

 TYPE\_LSOBJECT  

 TYPE\_HTML  

TYPE\_SCHED\_LIST  

TYPE\_CALENDAR\_FORMAT  

  

      CLASS\_ERROR       -  Data type is TYPE\_ERROR  

  

      CLASS\_UNAVAILABLE         -  Data type is TYPE\_UNAVAILABLE  

  

      CLASS\_NUMBER     -  Data type is TYPE\_NUMBER or TYPE\_NUMBER\_RANGE  

  

      CLASS\_TIME           -  Data type is TYPE\_TIME or TYPE\_TIME\_RANGE  

  

      CLASS\_TEXT           -  Data type is TYPE\_TEXT or TYPE\_TEXT\_LIST  

  

      CLASS\_FORMULA   -  Data type is TYPE\_FORMULA  

  

      CLASS\_USERID       -  Data type is TYPE\_USERID  

  

      CLASS\_MASK          -  Masks out the lower byte of an item's data type to
reveal the item's class  

  




**Description :**



Classes are
defined to be the "generic" classes of data type that the internal
formula computation mechanism recognizes when doing recalcs.


 **See Also :**


**[TYPE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/002100600028002B85255E2D0079321C)**



----------------------------------------------------------------------------------------------------------


 





