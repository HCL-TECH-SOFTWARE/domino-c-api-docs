




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Data Type : Signal Handler; User
Registration**



**REGSIGNALPROC** **-** Callback
function used to display status messages  for the user registration functions.


**----------------------------------------------------------------------------------------------------------**



**#include
<reg.h>**



**Definition :**



typedef void
(LNCALLBACKPTR REGSIGNALPROC)(


   char far \* Message)
/\* Status string that may be displayed by


                          the
function \*/


 


**Description :**



This data
structure defines the syntax of the user-defined callback function called by
the user registration functions.  Specify a function that conforms to this
syntax as the signalstatus parameter to REGNewWorkstation and other
registration functions.  The user registration functions will call your
function to display status messages.


 **Sample Usage :**


/\* This code snippet
illustrates how to use the callback   

   function in a Window's program  \*/  

  

    :  

    :  

  

FARPROC lpProc;  

HCERTIFIER hCertCtx;  

STATUS error;  

   

/\* Prepare to call REGNewWorkstation() to create and register   

   a new user. First get the Organization Unit Certifier   

   context for ABCorp, Sales Unit. Then, pass this certifier   

   context as input to REGNewWorkstation(). It will certify   

   the new user with this certifier.   

\*/  

  

if (error = GetCertCtx(ORGUNIT\_CERT\_ID, &hCertCtx, "abcorp"))  

{  

   return (ERR(error));  

}  

  

  

lpProc = MakeProcInstance(REGCallback, hInst);     

  

error = REGNewWorkstation (  

   hCertCtx,              /\* certifier context \*/  

   KFM\_IDFILE\_TYPE\_DERIVED, /\* derived from certifier context \*/  

   ServName,              /\* Registration server \*/  

   "Inside Sales",        /\* Org Unit - provides uniqueness  

                             to the name \*/  

   "Doe",                 /\* Last name \*/  

   "Jayne",               /\* First name \*/  

   NULL,                  /\* no middle initial \*/  

   NULL,                  /\* no password initially \*/  

   USER\_ID,               /\* ID file name \*/  

   "323 West",            /\* location - optional \*/  

   NULL,                  /\* comment - optional \*/  

   MAILSYSTEM\_NOTES,      /\* mail system  \*/  

   ServName,              /\* mail server name \*/  

   MAILFILENAME,          /\* pathname of mail file \*/  

   NULL,                  /\* forward address - optional \*/  

   fREGCreateIDFileNow |  /\* flags \*/  

   fREGUSARequested    |  

   fREGCreateMailFileNow |  

   fREGCreateAddrBookEntry,  

   0,                        /\* minimum password length \*/  

   (REGSIGNALPROC) lpProc,   /\* pointer to callback function \*/  

   FullDBPath);              /\* returned pathname of file where  

                                error occurred \*/  

  

/\* Free the certifier context \*/  

SECKFMFreeCertifierCtx (hCertCtx);  

  

FreeProcInstance(lpProc);  

  

    :  

    :


 **See Also :**


**[REGNewWorkstation](REGNewWorkstation.md)**


**[REGNewServer](REGNewServer.md)**


**[REGNewCertifier](REGNewCertifier.md)**



----------------------------------------------------------------------------------------------------------


 





