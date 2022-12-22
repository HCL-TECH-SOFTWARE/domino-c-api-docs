




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




**Initial Release 5.0**



**Symbolic Value : User Registration**



**fREGExtxxx** **-** Flag options
for REGNewUser.


**----------------------------------------------------------------------------------------------------------**



**#include <reg.h>**


 **Symbolic Values :**      fREGExtCreateMailFTIndex   -  This flag should be set during
REGNewUser for mail creation.  

  

      fREGExtReturnPersonNote   -  This flag is set during REGNewUser if the
caller wants the note handle of the new person document.  

  

      fREGExtEnforceUniqueShortName    -  Use this flag to enforce the
shortname of the user.  

  

      fREGExtRoamingUserNow    -  Create roaming files now - person is created
with ability to roam.  

  

      fREGExtRoamingFilesUsingAdminp   -  Create roaming files via the
administration process - person is created with ability to roam.  

  

      fREGExtCreateINetKeyPair   -  Add the INetPublicKey to the person
document.  

  

      fREGExtMailReplicasUsingAdminp    -  Create mail replicas via the
administration process.  

  

      fREGExtRoamingReplicasUsingAdminp         -  Create roaming replicas via
the administration process.  

  

      fREGExtRegUsingPolicy       -  Person registration will use the policy
settings (registration) as parameter values for registration.  

  




**Description :**



These values
specify options for the FLAGS parameter of REGNewUser.


 **See Also :**


**[REGNewUser](REGNewUser.md)**


**[REGNewPerson](REGNewPerson.md)**



----------------------------------------------------------------------------------------------------------


 





