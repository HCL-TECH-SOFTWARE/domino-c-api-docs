




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




**Initial Release 4.6.1**



**Function : Profile Document**



**NSFProfileGetField** **- Get the
value of the field in a profile document.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFProfileGetField(**  

      DBHANDLE  hDB,  

      const char \*ProfileName,  

      WORD  ProfileNameLength,  

      const char \*UserName,  

      WORD  UserNameLength,  

      const char \*FieldName,  

      WORD  FieldNameLength,  

      WORD \*retDatatype,  

      BLOCKID \*retbhValue,  

      DWORD \*retValueLength**);**



**Description :**



Get the
value of the field in a profile document.  The profile document is opened
automatically if it is not already open.           


 


**Parameters :**



Input :  

hDB  -  Handle to the database where the profile document exists.  

  

ProfileName  -  Name of the profile.  

  

ProfileNameLength  -  Length of the profile name.  

  

UserName  -  Name of the user of this profile.  Optional - may be NULL.  

Note:  For each profile document created, the UserName is contained in a
TYPE\_TEXT field named $Name.  This $Name field is represented as
"prefix\_nnnprofilename\_username" where:  

     prefix = the type of document  

     nnn = 3 digit character representation of the length of the profile name  

     profilename = the name of the profile document  

     username = the UserName of the profile  

An example of this field from a "Calendar Profile" document created
from the Notes client would be, $profile\_015calendarprofile\_.  Here the
UserName is blank since this profile was created with the Notes client. 
Therefore to retrieve this profile, use NULL for UserName.  Another example of
a profile document where UserName may be blank is the "Delegation
Profile".  This profile is also created using the Notes client.  

  

UserNameLength  -  Length of the user name.  Optional - may be zero.  

  

FieldName  -  Name of the field of which to get the value.  

  

FieldNameLength  -  Length of the field name.  

  




Output :  

(routine)  -  NOERROR - Successfully returned the field wanted from the profile
document.  

ERR\_xxx - Use OSLoadString to display the error returned.  

  

  

retDatatype  -  Datatype of the item.  

  

retbhValue  -  BLOCKID pointing to the value of the item, including the
datatype word.  

  

retValueLength  -  Length of the value of the item, including the datatype
word.  

  




 **Sample Usage :**



char
UserName[]="John Doe";


char
FieldBuffer[128];


char
\*pData;


 


/\* Open the
database. \*/  

      

if (error = NSFDbOpen (path\_name, &db\_handle))  

{  

        print\_api\_error (error);


        NotesTerm();  

        exit (EXIT\_FAILURE);  

}


 


/\* Get the
"Owner" item from "John Doe's" "CalendarProfile"
document \*/


 


if( error =
NSFProfileGetField( db\_handle, MAIL\_CALENDAR\_PROFILE\_FORM,


                                       
(WORD) strlen(MAIL\_CALENDAR\_PROFILE\_FORM),  

                                        UserName, (WORD) strlen(UserName),  

                                        MAIL\_CALENDAR\_PROFILE\_OWNER\_ITEM,  

                                        (WORD)
strlen(MAIL\_CALENDAR\_PROFILE\_OWNER\_ITEM),  

                                        &retDataType,  

                                        &retbhValue,  

                                        &retValueLength))  

{  

        print\_api\_error (error);


        NSFDbClose(
db\_handle );  

        NotesTerm();  

        exit (EXIT\_FAILURE);  

}  

  

if( retDataType == TYPE\_TEXT )


{


        pData
= OSLockBlock( char, retbhValue );  

        pData += sizeof(WORD);                               /\* step over data
type word \*/


 


        memmove(
FieldBuffer, pData, (int) (retValueLength - sizeof(WORD)));  

        FieldBuffer[retValueLength - sizeof(WORD)] = '\0';  

        OSUnlockBlock( retbhValue);


 


        printf("\nValue
of Field Requested is %s.\n", FieldBuffer);


}


 


 **See Also :**


**[NSFProfileSetField](NSFProfileSetField.md)**



----------------------------------------------------------------------------------------------------------


 





