




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



**REG\_ID\_INFO** **-** Structure
that defines ID registration information.


**----------------------------------------------------------------------------------------------------------**



**#include
<reg.h>**



**Definition :**



typedef struct


        {


        DWORD   Size;                         /\*
size of this structure - must initialize with sizeof (REG\_ID\_INFO) \*/


        WORD    Type;                         /\*
see KFM\_IDFILE\_??? \*/


        WORD    KeyWidth;                     /\*      The
only valid values are (see bsafe.h):


                                                     0
- default


                                                     KEYBITS\_630
- Compatible with all releases


                                                     KEYBITS\_1024
- Compatible with R6 and later


                                                     KEYBITS\_2048
- Compatible with R7 and later


                                             \*/


        WORD    PasswordKeyWidth;             /\*      The
only valid values are (see bsafe.h):


                                                     KEYBITS\_0
- default (means 64 bits for KeyWidth < 1024 else 128 bits)


                                                     KEYBITS\_64
- 64 bits


                                                     KEYBITS\_128
- 128 bits 


                                             \*/


        char    \*FileName;


        DWORD   Reserved[4];


        void    \*pReserved[4];


        }
REG\_ID\_INFO;


 


 


 


**Description :**




This
structure defines ID registration information for the REGNewPerson,
REGNewCertifierExtended, and REGNewServerExtended2 functions.  The entire
structure must


be
initialized to zero.


 


The fields
in the structure are (all fields that are not used must be NULL/O):


 


Size                                    Size
of this structure - must be initialized with sizeof (REG\_ID\_INFO)


Type                                  See
Symbolic Value KFM\_IDFILE\_TYPE\_XXX, in this reference and base on the entity
being registered 


KeyWidth                            Key
width in bits - valid values: 


                                                      0
- default


                                                      630
- Compatible with all releases


                                                      1024
- Compatible with R6 and later


PasswordKeyWidth             Encryption
strength in bits:


                                                      0
- default


                                                      64


                                                      128


FileName                            The
pathname of the new ID file. If the fREGCreateIDFileNow flag is not specified,
then this file must exist. 


Reserved                            Reserved
- must be 0


pReserved                          Reserved
- must be NULL


 


 **See Also :**


**[REGNewCertifierExtended](REGNewCertifierExtended.md)**


**[REGNewPerson](REGNewPerson.md)**


**[REGNewServerExtended2](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/3D8273E3BCDC943485256EBD005634A5)**



----------------------------------------------------------------------------------------------------------


 





