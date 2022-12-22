




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



**REG\_SERVER\_INFO** **-** Structure
that defines server registration information.


**----------------------------------------------------------------------------------------------------------**



**#include
<reg.h>**



**Definition :**



typedef struct


        {


        DWORD   Size;          /\*
size of this structure - must initialize with sizeof (REG\_SERVER\_INFO) \*/


 


        /\*
server name information \*/


        char    \*Name;


        char    \*OrgUnit;


        char    \*Title;


        char    \*DomainName;


        char    \*NetworkName;


        char    \*AdminName;


 


        /\*
server password information \*/


        char                   \*Password;


        WORD                   PasswordQuality;


 


        /\*
control flags \*/


        REGFlags               Flags;


 


        /\*
server internet information \*/


        char    \*HostName;


        HCERTIFIER
hInternetCertCtx;


        char    \*KeyringFileName;


        char    \*KeyringPassword;


 


        /\*
ID file information \*/


        REG\_ID\_INFO            \*IDInfo;


 


        /\*
generic information \*/


        REG\_MISC\_INFO  \*MiscInfo;


 


        DWORD   Reserved[4];


        void    \*pReserved[4];


        }
REG\_SERVER\_INFO;


 


 


 


**Description :**




This
structure defines server registration information for the REGNewServerExtended2
function.  The entire structure must


be
initialized to zero.


 


The fields
in the structure are (all fields that are not used must be NULL/O):


 


Size                        Size
of this structure - must be initialized with sizeof (REG\_SERVER\_INFO)


Name                     The
name of the new server


OrgUnit                 (Optional). 
Organizational unit of the new server (hierarchical only and in addition to
that derived from the certifier context).


ServerTitle 
           (Optional).  The server title to be stored in the Domino Directory


DomainName         The
Notes domain of the new server


NetworkName 
      (Optional).  The name of the network for the new server.   Do not pass in
a literal constant.


AdminName           (Optional). 
The name of the administrator for the new server.


Password              (Optional). 
The password for the new server


PasswordQuality     Quality
of password required for this server (0 - 16)


Flags                     Flags
that are set to specify options.  See Symbolic Value, fREGxxx, in this
reference.  Note that registration flags pertaining to the creation of a mail
file  (fREGCreateMailFileNow                            and
fRegCreateMailFileLocally) are not applicable to this function.


Hostname               (Optional). 
The hostname of this server for SSL purposes.  Required when setting up server
SSL


hInternetCertCtx     (Optional). 
The internet certifier context for SSL purposes.  Required when setting up
server SSL


KeyringFileName    (Optional). 
The filename of the keyring created for SSL purposes.  


KeyringPassword    (Optional). 
The password of the keyring file created for SSL purposes.  Required when
setting up server SSL.


IDInfo                     (Optional). 
Pointer to a structure of REG\_ID\_INFO


MiscInfo                 (Optional). 
Pointer to a structure of REG\_MISC\_INFO


Reserved                Reserved
- must be 0


pReserved              Reserved
- must be NULL


 


 **See Also :**


**[fREGxxx](fREGxxx.md)**


**[REGNewServerExtended2](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/3D8273E3BCDC943485256EBD005634A5)**


**[REG\_ID\_INFO](REG_ID_INFO.md)**


**[REG\_MISC\_INFO](REG_MISC_INFO.md)**



----------------------------------------------------------------------------------------------------------


 





