




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




 


**Symbolic Value : User Registration**



**KFM\_IDFILE\_TYPE\_xxx** **-** Various
types of IDs that can be created.


**----------------------------------------------------------------------------------------------------------**



**#include <kfm.h>**


 **Symbolic Values :**      KFM\_IDFILE\_TYPE\_FLAT    -  Flat name space (V2 compatible)  

  

      KFM\_IDFILE\_TYPE\_STD      -  Standard (user/server hierarchical)  

  

      KFM\_IDFILE\_TYPE\_ORG     -  Organization certifier  

  

      KFM\_IDFILE\_TYPE\_ORGUNIT         -  Organizational unit certifier  

  

      KFM\_IDFILE\_TYPE\_DERIVED          -  Derived from certifer context.
(hierarchical => STD; non-hierarchical => FLAT)  

  

      KFM\_IDFILE\_TYPE\_INET    -  Internet certifier.  

  




**Description :**



Constants
used to indicate various types of IDs that can be created.


 **See Also :**


**[REGNewCertifier](REGNewCertifier.md)**


**[REGNewServer](REGNewServer.md)**


**[REGNewServerExtended](REGNewServerExtended.md)**


**[REGNewWorkstation](REGNewWorkstation.md)**


**[REGNewWorkstationExtended](REGNewWorkstationExtended.md)**



----------------------------------------------------------------------------------------------------------


 





