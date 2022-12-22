




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



**REG\_CERTIFIER\_INFO** **-** Structure
that defines certifier registration information.


**----------------------------------------------------------------------------------------------------------**



**#include
<reg.h>**



**Definition :**



typedef struct


        {


        DWORD                  Size;                  /\*
size of this structure - must initialize with sizeof (REG\_CERTIFIER\_INFO) \*/


 


        /\*
certifier name information \*/


        char
                  \*Country;


        char
                  \*Org;


        char
                  \*OrgUnit;


 


        /\*
certifier password information \*/


        char                   \*Password;


        WORD                   PasswordQuality;


 


        /\*
certifier mail information \*/


        char
                  \*MailServerName;


        char
                  \*MailFileName;


        char
                  \*ForwardAddress;


 


        /\*
control flags \*/


        REGFlags               Flags;


 


        /\*
ID file information \*/


        REG\_ID\_INFO            \*IDInfo;


 


        /\*
generic information \*/


        REG\_MISC\_INFO  \*MiscInfo;


        


        DWORD   Reserved[4];


        void    \*pReserved[4];


        }
REG\_CERTIFIER\_INFO;


 


 


 


**Description :**




This
structure defines certifier registration information for the
REGNewCertifierExtended function.  The entire structure must


be
initialized to zero.


 


The fields
in the structure are (all fields that are not used must be NULL/O):


 


Size                        Size
of this structure - must be initialized with sizeof (REG\_CERTIFIER\_INFO)


Country                  (Optional). 
Country code of certifier.


Org                       Organization
of the new certifier if of type ORG.


OrgUnit                  Organization
unit of the new certifier if of type ORGUNIT.


Password              (Optional). 
The password for the new certifier


PasswordLength     Quality
of password required for this certifier (0 - 16)


MailServerName 
  (Optional).  Name of mail server where the mail file is to be created.  If
the flag fREGCreateMailFileNow is specified and no mail server name is supplied
(the pointer is NULL), the                                   mail file will be
created on the local system.


MailFileName 
       (Optional;  required if the flag fREGCreateMailFileNow is specified). 
Name of the mail file to create.


ForwardAddress 
  (Optional).  Another Notes domain or foreign mail gateway where mail is to be
forwarded.


Flags                      Flags
that are set to specify options.  See Symbolic Value, fREGxxx, in this
reference


IDInfo                     (Optional).
pointer to a structure of REG\_ID\_INFO


MiscInfo                 (Optional).
Pointer to a structure of REG\_MISC\_INFO


Reserved                Reserved
- must be 0


pReserved              Reserved
- must be NULL


 


 **See Also :**


**[REGNewCertifierExtended](REGNewCertifierExtended.md)**



----------------------------------------------------------------------------------------------------------


 





