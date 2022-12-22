




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




 


**Symbolic Value : Import/Export**



**IXFLAG\_xxx** **-** Flags passed
to all file import/export libraries


**----------------------------------------------------------------------------------------------------------**



**#include <ixport.h>**


 **Symbolic Values :**      IXFLAG\_FIRST         -  The file currently being imported or
exported is the first of a sequence of files to be processed.  

  

      IXFLAG\_LAST          -  The file currently being imported or exported is
the last of a sequence of files to be processed.  

  

      IXFLAG\_APPEND     -  The file currently being exported should be appended
to the output file.  

  




**Description :**



These values
are passed to the main entry point of all import/export libraries in the Flags
parameter (second argument). Use these flags to modify the behavior of the
import or export library when importing or exporting multiple files in one
step.  

  

An edit-level import library that imports multiple files in one step normally
creates the output file if IXFLAG\_FIRST is set, but if IXFLAG\_FIRST is not set,
it normally opens the existing output file and seeks to the end.  

  

An edit-level export libraray normally opens the specified output file and
seeks to the end if the output file already exists and the flag IXFLAG\_APPEND
is set. Otherwise, it may create the output file.  

  

A view-level import library may query the user for settings via a dialog box if
IXFLAG\_FIRST is set. The import library may allocate a buffer to save these
settings, then subsequently use the saved settings if IXFLAG\_FIRST is not set.
When IXFLAG\_LAST is set, the library may free the buffer used to save the
settings.


 **Sample Usage :**


STATUS LNPUBLIC 
MainEntryPoint(EDITIMPORTDATA \*EditorData,  

                                   WORD Flags,  

                                   HMODULE hModule,  

                                   char \*AltLibraryName,  

                                   char \*FileName)  

{  

    STATUS          error, rerror;  

    HANDLE          hCompound;  /\* handle to Compound Text context \*/  

    COMPOUNDSTYLE   Style;  

    DWORD           dwStyleID;  

    int             hInputFile, hOutputFile, hCDTextFile;  

    HANDLE          hReturnCD;  

    DWORD           dwReturnCDLen;  

    WORD            wRead;  

    char            achReturnCDFileName[MAXPATH];  

    char           \*pCDText;  

  

    /\* If processing the first input file, create the output file. \*/  

  

    if (Flags & IXFLAG\_FIRST)  

    {  

        if (error = IeditFileCreate( EditorData->OutputFileName,  

                                    &hOutputFile ))  

        {  

            IeditMessageBox("Unable to create temporary file",error);  

            goto Exit0;  

        }  

    }  

    else  

    {  

    /\* Else output file already exists. Open and seek to the end.\*/  

  

        if (error = IeditFileOpenForWrite( EditorData->OutputFileName,  

                                    &hOutputFile ))  

        {  

            IeditMessageBox ("Unable to open temporary file", error);  

            goto Exit0;  

        }  

    


 **See Also :**


**[IXENTRYPROC](IXENTRYPROC.md)**


**[EDITEXPORTDATA](EDITEXPORTDATA.md)**


**[EDITIMPORTDATA](EDITIMPORTDATA.md)**



----------------------------------------------------------------------------------------------------------


 





