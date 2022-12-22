




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



**REG\_MAIL\_INFO\_EXT** **-** Structure
that defines User Registration Extended Mail Creation Information.


**----------------------------------------------------------------------------------------------------------**



**#include
<reg.h>**



**Definition :**



typedef struct


        {


        DWORD   Size;                  /\*
size of this structure - must initialize with sizeof (REG\_MAIL\_INFO\_EXT) \*/


        WORD
   MailSystem;


        WORD
   MailOwnerAccess;


        DWORD   DbQuotaSizeLimit;


        DWORD   DbQuotaWarningThreshold;


        char
   \*pMailServerName;


        char
   \*pMailFileName;


        char
   \*pMailTemplateName;


        char
   \*pMailForwardAddress;


        char
   \*pMailACLManager;


        DHANDLE hReplicaServers;


        WORD    OnDuplicate;           /\*
one of REG\_FILE\_DUP\_XXX \*/


 


        DWORD   Reserved[4];


        void    \*pReserved[4];


        }
REG\_MAIL\_INFO\_EXT;


 


 


 


**Description :**



This
structure defines user registration extended mail creation information. for the
REGNewPerson function.  The entire structure must be initialized to zero.


 


 The fields
in the structure are (all fields that are not used must be NULL/O):


 


Size                                                Size
of this structure - must be initialized with sizeof (REG\_MAIL\_INFO\_EXT).


MailSystem                                    Defines
the type of mail system.


MailOwnerAccess                           Mail
owner's ACL priviledges (see REG\_MAIL\_OWNER\_ACL\_xxx).


DbQuotaSizeLimit                           Mail
file's size limit.                               


DbQuotaWarningThreshold             Mail
file's warning threshold size.


pMailServerName                           Name
of server the person's mail file will reside on.


pMailFileName                                Path
name of 's mail file.


pMailTemplateName                             
Name of mail template.


pMailForwardAddress                     Forwarding
address of  a Domino domain or foreign mail gateway.


pMailACLManager                          ACL
Manager's name.   


hReplicaServers                             (Optional.)
Handle to a text list of server names where replica stubs of the mail file
should be  

                               created.  The list should be constructed with
ListAllocate and ListAddEntry.  


   
OnDuplicate                   one of REG\_FILE\_DUP\_XXX.


Reserved                                        Reserved
- must be 0.


pReserved                                      Reserved
- must be NULL.


 


 **See Also :**


**[ListAddEntry](ListAddEntry.md)**


**[ListAllocate](ListAllocate.md)**


**[READ\_MASK\_xxx](READ_MASK_xxx.md)**


**[REGNewPerson](REGNewPerson.md)**


**[REG\_FILE\_DUP\_xxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/F5B76F9FC1F19DDE4825709C005227B9)**


**[REG\_MAIL\_OWNER\_ACL\_xxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/75E7BF1A835CC228852566C5005810C6)**



----------------------------------------------------------------------------------------------------------


 





