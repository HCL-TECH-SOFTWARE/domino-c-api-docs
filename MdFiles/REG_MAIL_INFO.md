




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



**REG\_MAIL\_INFO** **-** Structure
that defines User Registration Mail Creation Information. 


**----------------------------------------------------------------------------------------------------------**



**#include
<reg.h>**



**Definition :**



typedef struct {  

   WORD   MailSystem;


   WORD  
MailOwnerAccess;  

   DWORD  DbQuotaSizeLimit;  

   DWORD  DbQuotaWarningThreshold;  

   char \* pMailServerName;  

   char \* pMailFileName;  

   char \* pMailTemplateName;  

   char \* pMailForwardAddress;


   char \*
pMailACLManager;  

   DWORD  Spare[4];


} REG\_MAIL\_INFO;


 


**Description :**



This
structure is used for creating a user's mail file with the REGNewUser function.



 


        The
fields in the structure are:


 


        
MailSystem                                   defines the type of mail system.


        
MailOwnerAccess              mail owner's ACL priviledges (see REG\_MAIL\_OWNER\_xxx).


        
DbQuotaSizeLimit              mail file's size limit.                               


        
DbQuotaWarningThreshold mail file's warning threshold size.


        
pMailServerName              name of server the user's mail file will reside
on.


        
pMailFileName                               path name of user's mail file.


        
pMailTemplateName                      name of mail template


        
pMailForwardAddress                    forwarding address of  a Domino domain
or foreign mail gateway.


        
pMailACLManager             ACL Manager's name.   


        
Spare


 


 **See Also :**


**[REGNewUser](REGNewUser.md)**


**[REG\_MAIL\_OWNER\_ACL\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/75E7BF1A835CC228852566C5005810C6)**



----------------------------------------------------------------------------------------------------------


 





