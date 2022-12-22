




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



**NSFProfileEnum** **-
Enumerates profile documents with the specified profile name.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFProfileEnum(**  

      DBHANDLE  hDB,  

      const char \*ProfileName,  

      WORD  ProfileNameLength,  

      NSFPROFILEENUMPROC  Callback,  

      void \*CallbackCtx,  

      DWORD  Flags**);**



**Description :**



Enumerates
through all profile documents in the database which have the specified profile
name.  If the given profile is found then the function calls a user-supplied
routine (an action routine) for that profile. 


 


**Parameters :**



Input :  

hDB  -  Handle to the database where the profile document exists.  

  

ProfileName  -  Name of the profile.  To enumerate all profile documents within
a database, use NULL for ProfileName.  

  

ProfileNameLength  -  Length of the profile name.  

  

Callback  -  Enumeration routine to process each profile that is found.  

  

CallbackCtx  -  Caller defined context block that is passed to the enumeration
routine.  Optional, may be NULL.  

  

Flags  -  (Reserved for future use.)  Must be 0.  

  




Output :  

(routine)  -  NOERROR - No errors occurred through the execution of
NSFProfileEnum or any of the calls to the action routine.  

ERR\_xxx - Use OSLoadString to display the error returned.  

  

  




 **Sample Usage :**



/\* Open the
database. \*/  

      

if (Error = NSFDbOpen (path\_name, &hDB))  

{  

        fprintf( stderr, "Error encountered opening the
database.\n");


        PrintAPIError
(Error);  


        NotesTerm();


        return
(1);


}


/\* 


 \*
Enumerate all "CalendarProfile" Documents for this Database. 


 \* Action
Routine DumpProfile() will be called for each "CalendarProfile"


 \* document
found.


 \*/


if (Error =
NSFProfileEnum( hDB, MAIL\_CALENDAR\_PROFILE\_FORM,


                                 
(WORD) strlen(MAIL\_CALENDAR\_PROFILE\_FORM),  

                                  DumpProfile, NULL, 0 ))  

{  

        fprintf( stderr, "Error encountered searching for profile
information.\n");


        NSFDbClose(
hDB );  

        PrintAPIError (Error);  


        NotesTerm();


        return
(1);


}


 **See Also :**


**[NSFPROFILEENUMPROC](NSFPROFILEENUMPROC.md)**



----------------------------------------------------------------------------------------------------------


 





