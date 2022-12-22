




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




**Initial Release 4.6.2**



**Data Type : Administration Process**



**ADMINReqParams** **-** Parameters
of an administration request


**----------------------------------------------------------------------------------------------------------**



**#include
<adminp.h>**



**Definition :**



typedef struct {


   DWORD
Flags;             /\* Reserved \*/


   DWORD
dwDeleteInNABType; /\* DELETE\_xxxx\_IN\_NAB defined above \*/


    char far
\*chGroupName;   /\* if dwDeleteInNABType equals


                              
DELETE\_PERSON\_IN\_NAB a pointer to a


                              
group (termination perhaps) to have


                              
the name added \*/


   char far
\*chAltName;     /\* if dwDeleteInNABType equals


                              
DELETE\_PERSON\_IN\_NAB a pointer to


                               the
person's Alternate Name \*/


   char far
\*chFirstName;   /\* for ADMINReqMoveComplete, a pointer


                              
to a new first name for the


                              
person \*/


   char far
\*chMiddleInitial; /\* for ADMINReqMoveComplete, a


                              
pointer to a new middle initial for


                              
the person \*/


   char far
\*chLastName;    /\* for ADMINReqMoveComplete, a pointer


                              
to a new last name for the person \*/


   char far
\*chAltCommonName; /\* for ADMINReqRename,


                              
ADMINReqRecertify, and


                              
ADMINReqMoveComplete, a pointer to a


                              
new alternate common name for the


                               person
\*/  


   char far
\*chAltOrgUnitName; /\* for ADMINReqRename,


                              
ADMINReqRecertify, and


                              
ADMINReqMoveComplete, a pointer to a


                              
new alternate org unit for the


                              
person \*/  


   char far
\*chAltLanguage; /\* for ADMINReqRename,


                              
ADMINReqRecertify, and


                              
ADMINReqMoveComplete, a pointer to a


                              
new alternate language for the


                              
person \*/ 


   BOOL
fDontUseV1ChangeRequest; /\* for ADMINReqMoveUserInHier,


                              
TRUE indicates that support for a


                               simultaneous
hierarchy move and name


                              
change.  Recognized only by v5.02


                              
and above clients and servers \*/


 


/\* 5.x
structure ended here.  The following fields were added for Rnext \*/


 


        DBHANDLE
dbhDirectory; /\* for ADMINReqDeleteInNAB, a handle to 


                                        
the directory from which the Person, 


                                        
Server, or Group is to be deleted if 


                                        
the target directory is not names.nsf \*/


 


} ADMINReqParams;


 


**Description :**



This
structure contains the parameters of an administration request.  When setting
this structure, first initialize the values of structure members to 0.


 **See Also :**


**[ADMINReqChkAccessMoveReplica](ADMINReqChkAccessMoveReplica.md)**


**[ADMINReqChkAccessNewReplica](ADMINReqChkAccessNewReplica.md)**


**[ADMINReqDeleteInACL](ADMINReqDeleteInACL.md)**


**[ADMINReqDeleteInNAB](ADMINReqDeleteInNAB.md)**


**[ADMINReqMoveComplete](ADMINReqMoveComplete.md)**


**[ADMINReqMoveUserInHier](ADMINReqMoveUserInHier.md)**


**[ADMINReqRecertify](ADMINReqRecertify.md)**


**[ADMINReqRename](ADMINReqRename.md)**


**[ADMINReqUpgradeToHier](ADMINReqUpgradeToHier.md)**



----------------------------------------------------------------------------------------------------------


 





