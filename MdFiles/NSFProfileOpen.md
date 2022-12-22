




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



**NSFProfileOpen** **- Open a
profile document.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFProfileOpen(**  

      DBHANDLE  hDB,  

      const char \*ProfileName,  

      WORD  ProfileNameLength,  

      const char \*UserName,  

      WORD  UserNameLength,  

      BOOL  CopyProfile,  

      NOTEHANDLE \*rethProfileNote**);**



**Description :**



Open a
profile document.  If a profile for the specified profile name/user pair does
not exist, one is created.  Author access is the minimum access required to
create a profile document.


 


**Parameters :**



Input :  

hDB  -  Handle to the database where the profile document exists or is to be
created.  

  

ProfileName  -  Name of the profile.  

  

ProfileNameLength  -  Length of the profile name.  

  

UserName  -  Name of the user of this profile.  Optional - may be NULL.  

Note:  Author access is the minimum access required to create a profile
document.  With author access one can create profiles without a user name
specified; create profiles with a different user name specified; or create
profiles with their own user name specified.  For each profile document
created, the UserName is contained in a TYPE\_TEXT field named $Name.  This
$Name field is represented as "prefix\_nnnprofilename\_username" where:  

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

  

UserNameLength  -  Length of the user name.  Optional - may be zero  

  

CopyProfile  -  Must be TRUE.  The handle to a copy of the cached profile
document is returned.  

  




Output :  

(routine)  -  NOERROR - Successfully returned the handle to the profile
document.  

ERR\_xxx - Use OSLoadString to display the error returned.  

  

  

rethProfileNote  -  Handle to the profile document.  The caller is responsible
for closing the returned note handle when done with the note.  

  




 **Sample Usage :**



char
UserName[]="John Doe";


 


/\* Open the
database. \*/  

      

if ( Error = NSFDbOpen (path\_name, &hDB))  

{  

        fprintf( stderr, "Error encountered opening the
database.\n");


     
LAPI\_RETURN( ERR(Error));


}


 


/\* Open the
"CalendarProfile" Document for user "John Doe" \*/


 


if( Error =
NSFProfileOpen( db\_handle,  

                                  MAIL\_CALENDAR\_PROFILE\_FORM,(WORD)
strlen(MAIL\_CALENDAR\_PROFILE\_FORM),  

                                  UserName,(WORD) strlen(UserName),  

                                  TRUE, &note\_handle))  

{  

        fprintf( stderr, "Error encountered opening this Profile
Document.\n");


        NSFDbClose(
hDB );


     
LAPI\_RETURN( ERR(Error));


}


 **See Also :**


**[NSFProfileDelete](NSFProfileDelete.md)**


**[NSFProfileUpdate](NSFProfileUpdate.md)**



----------------------------------------------------------------------------------------------------------


 





