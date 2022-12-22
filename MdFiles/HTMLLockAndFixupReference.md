




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




**Initial Release 7.0.2**



**Function : HTML**



**HTMLLockAndFixupReference** **- Prepare a
reference for use.**


**----------------------------------------------------------------------------------------------------------**



**#include <htmlapi.h>**



STATUS
LNPUBLIC **HTMLLockAndFixupReference(**  

      MEMHANDLE  hRef,  

      HTMLAPIReference \*\*ppRef**);**



**Description :**



      1)
This needs to be called before the reference information can be accessed.


                        -
does not use HTMLHANDLE.  

       2) caller is responsible for unlocking the MEMHANDLE.


 


**Parameters :**



Input :  

hRef  -  memory handle to reference list (this was returned from
HTMLGetReference). If this is NULLMEMHANDLE then nothing happens (no error
status)  

  




Output :  

(routine)  -   NOERROR - Successful.  

  ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString to
interpret the error status as a string that you may display/log for the user.  

  

  

ppRef  -  ppRef - is the address of a pointer.  The pointer will be set to
point into the locked and fixedup memory.  If hRef is not null then this must
not be null  

  




 **Sample Usage :**


    STATUS rslt =
NOERRPR;


        FILE
\*m\_pLogFile;


        HTMLHANDLE
cvtr;


        DWORD   retval;


        unsigned
int refi;


        MEMHANDLE
hRef = 0;


        HTMLAPIReference
\*pRef = 0;


        char
\*LogInfoFormat = "%s%d\n"; 


        ............


        rslt
= HTMLGetProperty(cvtr, HTMLAPI\_PROP\_NUMREFS, &retval);


        fprintf(m\_pLogFile,
LogInfoFormat, "<HAPI:RefList count=", retval); 


 


        for
( refi = 0 ; refi < retval; refi++ )


        {


       
rslt = HTMLGetReference(cvtr, refi, &hRef);


               if(rslt)


               {


                       PrintLogInfo("Error
in Getting Reference");


                       return
rslt;


               }


               


               rslt
= HTMLLockAndFixupReference(hRef, &pRef);


               if(rslt)


               {


                       PrintLogInfo("Error
in Lock And Fixup Reference");


                       return
rslt;


               }


               


               fprintf(m\_pLogFile,
"%s%d%s\n", "<Reference N=\"", refi,
"\"");


               fprintf(m\_pLogFile,
LogInfoFormat, "  Type:     ", pRef->RefType);


               fprintf(m\_pLogFile,
LogInfoFormat, "  CmdId:    ", pRef->CommandId);


               fprintf(m\_pLogFile,
LogInfoFormat, "  Text:     ", pRef->pRefText);


               fprintf(m\_pLogFile,
LogInfoFormat, "  NTargets: ", pRef->NumTargets);


 


        //
show the target components of one reference.


       
nTargets = pRef->NumTargets;


        }


 **See Also :**


**[HTMLAPIReference](HTMLAPIReference.md)**


**[HTMLAPI\_REF\_TYPE](HTMLAPI_REF_TYPE.md)**


**[HTMLCreateConverter](HTMLCreateConverter.md)**


**[HTMLGetReference](HTMLGetReference.md)**



----------------------------------------------------------------------------------------------------------


 





