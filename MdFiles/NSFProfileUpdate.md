




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



**NSFProfileUpdate** **- Update an
open profile document.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFProfileUpdate(**  

      NOTEHANDLE  hProfile,  

      const char \*ProfileName,  

      WORD  ProfileNameLength,  

      const char \*UserName,  

      WORD  UserNameLength**);**



**Description :**



Update an
open profile document.  The items in the cached note for this profile document
are replaced with the items in the specified profile note.  In addition, the
database is updated using the specified profile note.  The caller is
responsible for closing the handle to the profile document after the update.


 


**Parameters :**



Input :  

hProfile  -  Handle of the profile document to be updated.  

  

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
UserName is blank since this profile was created with the Notes client.  Therefore
to retrieve this profile, use NULL for UserName.  Another example of a profile
document where UserName may be blank is the "Delegation Profile". 
This profile is also created using the Notes client.  

  

UserNameLength  -  Length of the user name.  Optional - may be zero  

  




Output :  

(routine)  -  NOERROR - Successfully updated the profile document.  

ERR\_xxx - Use OSLoadString to display the error returned.  

  

  




 **Sample Usage :**



char
ProfileName[]="MyProfile";


char
UserName[]="John Doe";


 


 


/\* Open
"MyProfile" Document for User John Doe.\*/


 


if( error =
NSFProfileOpen( db\_handle,  

                                  ProfileName,(WORD) strlen(ProfileName),  

                                  UserName,(WORD) strlen(UserName),  

                                  TRUE, &note\_handle))  

{  

        print\_api\_error (error);  

        NSFDbClose( db\_handle );


        NotesTerm();  

        exit (EXIT\_FAILURE);     

}


 


NSFNoteGetInfo(
note\_handle, \_NOTE\_ID, &note\_id );  

printf("\nProfile Note ID %lX \n", note\_id );


 


/\* Set
field ProfileOwner to the value in UserName \*/


 


if( error =
NSFItemSetText( note\_handle, "ProfileOwner",   

                                  UserName, (WORD) strlen(UserName)))  

{  

        print\_api\_error (error);


        NSFNoteClose(
note\_handle );


        NSFDbClose(
db\_handle );  

        NotesTerm();  

        exit (EXIT\_FAILURE);  

}


 


/\* Update
this Profile Document with the new information \*/


 


if( error =
NSFProfileUpdate( note\_handle, ProfileName,  

                                      (WORD) strlen(ProfileName),  

                                      UserName, (WORD) strlen(UserName)))  

{  

        print\_api\_error (error);


        NSFNoteClose(
note\_handle );


        NSFDbClose(
db\_handle );  

        NotesTerm();  

        exit (EXIT\_FAILURE);  

}


 


/\* Close
the note\_handle to this Profile Document \*/


NSFNoteClose(
note\_handle );


 **See Also :**


**[NSFProfileOpen](NSFProfileOpen.md)**



----------------------------------------------------------------------------------------------------------


 





