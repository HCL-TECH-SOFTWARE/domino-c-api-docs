




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




**Initial Release 5.0**



**Data Type : User Registration**



**REG\_USERNAME\_INFO** **-** Structure
that defines User Registration Name Information.


**----------------------------------------------------------------------------------------------------------**



**#include
<reg.h>**



**Definition :**



typedef struct {  

   char \* LastName;  

   char \* FirstName;  

   char \* MidInitial;  

   char \* OrgUnit;  

   char \* ShortName;  

   char \* AlternateName;  

   char \* AltOrgUnit;  

   char \* AltLanguage;  

   DWORD  Spare[4];


} REG\_USERNAME\_INFO;


 


**Description :**



This
structure defines User Name information for the REGNewUser function.


 


The fields
in this structure are:


 


LastName               last
name of the new user.


FirstName              first
name of the new user.


MidInitial                 middle
initial of the new user.


OrgUnit                  organizational
unit of the new user.


ShortName             


AlternateName


AltOrgUnit


AltLanguage


Spare


 **See Also :**


**[REGNewUser](REGNewUser.md)**



----------------------------------------------------------------------------------------------------------


 





