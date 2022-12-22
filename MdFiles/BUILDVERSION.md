




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




**Initial Release 5.0.9**



**Data Type : Database**



**BUILDVERSION** **-** Build
information structure


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfdb.h>**



**Definition :**




typedef
struct {


        DWORD   MajorVersion;  /\*      Major
version identifier \*/


        DWORD   MinorVersion;  /\*      Minor
version identifier \*/


        DWORD   QMRNumber;             /\*      Maintenance
Release identifier \*/


        DWORD   QMUNumber;             /\*      Maintenance
Update identifier \*/


        DWORD   HotfixNumber;  /\*      Hotfixes
installed on machine \*/      


        DWORD   Flags;         /\*      See
BUILDVERFLAGS\_xxx \*/


        DWORD   FixpackNumber; /\*      Fixpack
version installed on machine \*/


        DWORD   Spare[2];              /\*      Room
for growth \*/


        }
BUILDVERSION;


 


**Description :**



Structure
returned by NSFDbGetMajMinVersion to determine code level at runtime


 **See Also :**


**[BLDVERFLAGS\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/7737274DF2E422F185256A6800608933)**


**[NSFDbGetMajMinVersion](NSFDbGetMajMinVersion.md)**



----------------------------------------------------------------------------------------------------------


 





