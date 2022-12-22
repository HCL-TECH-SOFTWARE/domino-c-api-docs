




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




**Initial Release 7.0**



**Data Type : User Registration**



**REG\_MISC\_INFO** **-** Structure
that defines miscellaneous registration information.


**----------------------------------------------------------------------------------------------------------**



**#include
<reg.h>**



**Definition :**



typedef struct


        {


        DWORD          Size;                  /\*
size of this structure - must initialize with sizeof (REG\_MISC\_INFO) \*/


        char           \*Location;


        char           \*Comment;


        char           \*LocalAdminName;


        DWORD          Reserved[4];


        void           \*pReserved[4];


        }
REG\_MISC\_INFO;


 


 


 


**Description :**



This
structure defines miscellaneous registration information for the REGNewPerson,
REGNewCertifierExtended, and REGNewServerExtended2 functions.  The entire
structure must


be
initialized to zero.


 


The fields
in the structure are (all fields that are not used must be NULL/O):


 


Size                        Size
of this structure - must be initialized with sizeof (REG\_MISC\_INFO)


Location                 Location
string added to be added to the newly created note


Comment                Comment
string added to be added to the newly created note


LocalAdminName    Name
of the local administrator to be added to the newly created note


Reserved                Reserved
- must be 0


pReserved              Reserved
- must be NULL


 **See Also :**


**[REGNewCertifierExtended](REGNewCertifierExtended.md)**


**[REGNewPerson](REGNewPerson.md)**


**[REGNewServerExtended2](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/3D8273E3BCDC943485256EBD005634A5)**



----------------------------------------------------------------------------------------------------------


 





