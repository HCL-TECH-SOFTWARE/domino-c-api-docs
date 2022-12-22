




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




 


**Data Type : Import/Export**



**IXENTRYPROC** **-** defines the
arguments to an import/export library


**----------------------------------------------------------------------------------------------------------**



**#include
<ixport.h>**



**Definition :**



typedef STATUS
(LNCALLBACKPTR IXENTRYPROC)(  

    void far \*IXContext,      /\* See IXEDIT.H or IXVIEW.H \*/  

    WORD      Flags,          /\* IXFLAG\_xxx \*/  

    HMODULE   hModule,  

    char far \*AltLibraryName,  

    char far \*PathName);      /\* File to act upon \*/


 


**Description :**



This type
defines the syntax of the main entry point to an import/export library.  

  

A Notes import/export library must provide a function that conforms to this
syntax. A Notes import/export library is an executable program library that
Notes may load when needed to import or export Domino data to or from the view
or document level.  

  

Under Unix, the entry point function must be named "MainEntryPoint".
Under Windows, the function may have any name, but it must be the ordinal first
function exported by the library.  

  

Import functions read and interpret import files and convert them to Domino
format.  

  

Export functions read the specified Domino data and create output files.  

  

API programs may call any of the import or export modules provided with Notes
by loading the appropriate library, loading the address of the main entry point
function, and calling the function with the appropriate set of parameters.   

  

You may create your own custom import or export libraries by implementing a
function that conforms to the IXENTRYPROC syntax. Under Unix, your custom
import/export library must be a shared library, and the name of the main entry
point function must be "MainEntryPoint". Under Windows, your custom
import/export library must be a dynamic link library (DLL) and  it must export
the main entry point function as the ordinal first entry point in the DLL.
Install your custom library in the Notes program directory on the Notes
workstation and add the appropriate statement to the notes.ini file in the
Notes data directory on that system.  After restarting Notes, the user will see
the custom format option in the list of formats displayed in the File - Import
or File - Export dialog box in Notes.


 **Sample Usage :**



    /\* Use
OSLoadLibrary to load the import DLL and return a pointer to \*/  

    /\* the main entry point.                                             \*/  

     

    if (Error = OSLoadLibrary (ModuleName, (DWORD)0, &hmod,
&ProcAddress))  

    {  

        printf ("OSLoadLibrary failed.\n");  

        goto Done;  

    }


 


    /\* Set
up the EditImportData data structure with a Default          \*/  

    /\* filename for the library to do its report to.  If the import     \*/  

    /\* succeeds, this file will contain a set of compound document      \*/  

    /\* data strucures formatted in the  same manner as they would be    \*/  

    /\* if they were loaded in memory; the records start on even byte    \*/  

    /\* boundaries and contain a signature, length, the signature-       \*/  

    /\* specific data structure (if any), then the  signature-specific   \*/  

    /\* data.                                                            \*/


 


     
strcpy (EditImportData.OutputFileName, TempName);  

      printf ("Temp filename is %s.\n",
EditImportData.OutputFileName);  

     

    /\* Assign the default fontid \*/


 


     
EditImportData.FontID = DEFAULT\_FONT\_ID;


 


    /\* Call
the ProcAddress() function whose address we located within  \*/  

    /\* the DLL loaded above.  This is the SAME argument set that would  \*/  

    /\* be used by an import/export DLL written to handle a non-standard \*/  

    /\* file format.                                                     \*/  

    /\*                                                                  \*/  

    /\* The ProcAddress() function can import multiple files.  Since     \*/  

    /\* only one file is being imported in this example, the flags will  \*/  

    /\* indicate that the file is the first (and also last) file to be   \*/  

    /\* imported.                                                        \*/  

    /\*                                                                  \*/  

    /\* If a word processing document is being imported, the parameter   \*/  

    /\* SecondDLLName will be a pointer to the name of the second DLL    \*/  

    /\* that was entered on the command line.  See the README.TXT file   \*/  

    /\* for information on how to obtain the name of the 2nd DLL.  If a  \*/


    /\*
non-word processing document is being imported, this paramter    \*/  

    /\* was not entered on the command line, so SecondDLLName will be    \*/  

    /\* a pointer to a null string.                                      \*/  

     


 


    if
(Error = (\*ProcAddress) (&EditImportData,      

        IXFLAG\_FIRST | IXFLAG\_LAST,         /\* Both 1st and last import \*/  

        0,                                  /\* Use default hmodule      \*/  

        SecondDLLName,                      /\* 2nd DLL, if needed.      \*/  

        FileName))                          /\* File to import.          \*/  

        {  

            printf ("Call to DLL Entry point failed.\n");  

            goto Done;  

        }


 


    /\*
return the temp filename to calling routine \*/  

      

    strcpy (szTempName, EditImportData.OutputFileName);


 


Done:  

    /\* Free the DLL and return \*/  

        OSFreeLibrary(hmod);  

    return Error;


 


 **See Also :**


**[EDITEXPORTDATA](EDITEXPORTDATA.md)**


**[EDITIMPORTDATA](EDITIMPORTDATA.md)**


**[VIEWIXDATA](VIEWIXDATA.md)**


**[IXFLAG\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/70AB31E1305B39F68525600400775088)**



----------------------------------------------------------------------------------------------------------


 





