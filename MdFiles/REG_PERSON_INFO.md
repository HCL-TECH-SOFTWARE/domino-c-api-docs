




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



**REG\_PERSON\_INFO** **-** Structure
that defines person registration information.


**----------------------------------------------------------------------------------------------------------**



**#include
<reg.h>**



**Definition :**



typedef struct
reg\_person\_info


        {


        DWORD          Size;                  /\*
size of this structure - must initialize with sizeof (REG\_PERSON\_INFO) \*/


 


        /\*
person name information \*/


        char
          \*LastName;


        char
          \*FirstName;


        char
          \*MiddleName;


        char
          \*OrgUnit;


        char
          \*ShortName;


        char
          \*AlternateName;


        char           \*AltOrgUnit;


        char           \*InternetAddress;


 


        /\*
person password information \*/


        char           \*Password;


        WORD           PasswordQuality;


 


        /\*
person internet key information \*/


        WORD           INetKeyWidth;


 


        /\*
person language info \*/


        char           \*AltLanguage;


        char           \*PreferredLanguage;


 


        /\*
setup profile info \*/


        char           \*ProfileName;


 


        /\*
person group membership \*/


        void
          \*pGroupList;


 


        /\*
policy information \*/


        char           \*ExplicitPolicy;


        /\*
PolicyOverride function used when registering via policy
(fREGExtRegUsingPolicy) 


        as
a hook to modify registration items after policy evaluation but before 


        registration
processing


        


        NOTE:
As to not munge with internal memory, you should change pointers 


        to
point to your memory, you should not change callback memory:


        


        Example: 
To change the policy derived roaming subdirectory


        


        Don't
do change callback memory buffer:


               Cstrcpy
(PersonInfo->RoamingInfo->SubDirectory, "your new sub
directory");


 


        Make
the callback pointer point to your buffer:


               Cstrcpy
(szYourBuffer, "your new sub directory");


               PersonInfo->RoamingInfo->SubDirectory
= szYourBuffer;


        


        \*/


        STATUS
(LNCALLBACKPTR PolicyOverride)(HCERTIFIER hCertCtx, 


                                                     char
far \*\*RegServer,


                                                     struct
reg\_person\_info far \*PersonInfo);


 


        /\*
registration flags \*/


        REGFlags               Flags;


        REGFlagsExt            FlagsExt;


 


        REG\_MAIL\_INFO\_EXT      \*MailInfo;


 


        REG\_ID\_INFO            \*IDInfo;


        


        REG\_MISC\_INFO  \*MiscInfo;


 


        REG\_ROAMING\_INFO
\*RoamingInfo;


 


        /\*
when specified with fREGExtReturnPersonNote - return the person note and DB
handle \*/


        NOTEHANDLE
    \*phRetPersonNote;


        DBHANDLE
      \*phRetPersonNoteNAB;


 


        DWORD   Reserved[4];


        void    \*pReserved[4];


        char       
\*ForeignDN;     /\* distinguished name of the entry in a non-domino repository
(i.e LDAP DN) in Notes format \*/


               DIRENTRY   
\*phDirEntry;    /\* DIRENTRY of person to be returned to caller, see
fREGExtReturnPersonDirEntry \*/


        }
REG\_PERSON\_INFO;


 


 


 


**Description :**




This
structure defines person registration information for the REGNewPerson
function.  The entire structure must


be
initialized to zero.


 


The fields
in the structure are (all fields that are not used must be NULL/O):


Size                                    Size
of this structure - must be initialized with sizeof (REG\_PERSON\_INFO)


LastName                           Last
name of the new person.


FirstName                          First
name of the new person.


MiddleName                       Middle
name of the new person.


OrgUnit                              Organizational
unit of the new person.


ShortName                         Short
name of the new person.


AlternateName                    Alternate
name of the new person.


AltOrgUnit                          Alternate
org unit of the new person.


InternetAddress                  The
internet address of the new person.


Password                          (Optional). 
The password for the new server.


PasswordQuality                 Quality
of password required for this server (0 - 16).


INetKeyWidth                     (Optional)
The width of the internet key in bits (see fREGExtCreateINetKeyPair) Valid
values are:


                                                      0
- default


                                                      1024


AltLanguage                       The
alternate language of the new person.


PreferredLanguage             The
preferred language of the new person.


ProfileName 
                     (Optional).  Setup profile name(s).


pGroupList                                     (Optional). 
A pointer to a list of groups to add the new person to, constructed with
ListAllocate and ListAddEntries. 


ExplicitPolicy                      Explicit
policy to assign to the new person(and/or the explicit policy to use when
registering the new person (see fREGExtRegUsingPolicy).


PolicyOverride                    Callback
function used when registering person via policy (see fREGExtRegUsingPolicy) as
a hook to modify registration items after policy evaluation but before                                                          registration
processing.


      


                                          NOTE:
You should consider all memory passed back to be read only, you should change
pointers 


                                                      to
point to your memory, you should not change callback memory:


      


                                          Example: 
To change the policy derived roaming subdirectory.


      


                                          Don't
do change callback memory buffer:


                                                      Cstrcpy
(PersonInfo->RoamingInfo->SubDirectory, "your new sub
directory");


 


                                          Make
the callback pointer point to your buffer:


                                                      Cstrcpy
(szYourBuffer, "your new sub directory");


                                                      PersonInfo->RoamingInfo->SubDirectory
= szYourBuffer;


 


Flags                                 Flags
that are set to specify options.  See Symbolic Value, fREGxxx, in this
reference.


FlagsExt                             Flags
that are set to specify options.  See Symbolic Value, fREGExtxxx, in this
reference.


MailInfo                              (Optional)
Pointer to a REG\_MAIL\_INFO\_EXT strucutre


IDInfo                                 (Optional)
Pointer to a REG\_ID\_INFO structure


MiscInfo                             (Optional)
Pointer to a REG\_MISC\_INFO structure


RoamingInfo                       (Optional)
Pointer to a REG\_ROAMING\_INFO structure


phRetPersonNote                (Optional)
Pointer to receive the note handle of the new person document if the caller has
specified the REGExtFlag fREGExtReturnPersonNote.  Please see fREGExtxxx.


phRetPersonNoteNAB         (Optional)
Pointer to receive the database handle of the database where the new person
document was created.


Reserved                            Reserved
- must be 0


pReserved                          Reserved
- must be NULL


  
ForeignDN;                        Distinguished name of the entry in a
non-domino repository (i.e LDAP DN) in Notes format.


  
phDirEntry;                          /\* Internal use \*/


 **See Also :**


**[fREGExtxxx](fREGExtxxx.md)**


**[fREGxxx](fREGxxx.md)**


**[REGNewPerson](REGNewPerson.md)**



----------------------------------------------------------------------------------------------------------


 





