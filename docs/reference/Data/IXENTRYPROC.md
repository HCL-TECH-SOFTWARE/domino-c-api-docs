##### Data Type : Import/Export
##### IXENTRYPROC - defines the arguments to an import/export library
---
```
#include <ixport.h>
```
**Description :**

This type defines the syntax of the main entry point to an import/export 
library.

A Notes import/export library must provide a function that conforms to this 
syntax. A Notes import/export library is an executable program library that 
Notes may load when needed to import or export Domino data to or from the view 
or document level.

Under Unix, the entry point function must be named "MainEntryPoint". Under 
Windows, the function may have any name, but it must be the ordinal first 
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
```
    /* Use OSLoadLibrary to load the import DLL and return a pointer to */
    /* the main entry point.                                             */
   
    if (Error = OSLoadLibrary (ModuleName, (DWORD)0, &hmod, &ProcAddress))
    {
        printf ("OSLoadLibrary failed.\n");
        goto Done;
    }

    /* Set up the EditImportData data structure with a Default          */
    /* filename for the library to do its report to.  If the import     */
    /* succeeds, this file will contain a set of compound document      */
    /* data strucures formatted in the  same manner as they would be    */
    /* if they were loaded in memory; the records start on even byte    */
    /* boundaries and contain a signature, length, the signature-       */
    /* specific data structure (if any), then the  signature-specific   */
    /* data.                                                            */

      strcpy (EditImportData.OutputFileName, TempName);
      printf ("Temp filename is %s.\n", EditImportData.OutputFileName);
   
    /* Assign the default fontid */

      EditImportData.FontID = DEFAULT_FONT_ID;

    /* Call the ProcAddress() function whose address we located within  */
    /* the DLL loaded above.  This is the SAME argument set that would  */
    /* be used by an import/export DLL written to handle a non-standard */
    /* file format.                                                     */
    /*                                                                  */
    /* The ProcAddress() function can import multiple files.  Since     */
    /* only one file is being imported in this example, the flags will  */
    /* indicate that the file is the first (and also last) file to be   */
    /* imported.                                                        */
    /*                                                                  */
    /* If a word processing document is being imported, the parameter   */
    /* SecondDLLName will be a pointer to the name of the second DLL    */
    /* that was entered on the command line.  See the README.TXT file   */
    /* for information on how to obtain the name of the 2nd DLL.  If a  */
    /* non-word processing document is being imported, this paramter    */
    /* was not entered on the command line, so SecondDLLName will be    */
    /* a pointer to a null string.                                      */
     

    if (Error = (*ProcAddress) (&EditImportData,    
        IXFLAG_FIRST | IXFLAG_LAST,         /* Both 1st and last import */
        0,                                  /* Use default hmodule      */
        SecondDLLName,                      /* 2nd DLL, if needed.      */
        FileName))                          /* File to import.          */
        {
            printf ("Call to DLL Entry point failed.\n");
            goto Done;
        }

    /* return the temp filename to calling routine */
    
    strcpy (szTempName, EditImportData.OutputFileName);

Done:
    /* Free the DLL and return */
 OSFreeLibrary(hmod);
    return Error;

```
**See Also :**
[EDITEXPORTDATA](/reference/Data/EDITEXPORTDATA)
[EDITIMPORTDATA](/reference/Data/EDITIMPORTDATA)
[VIEWIXDATA](/reference/Data/VIEWIXDATA)
[IXFLAG_xxx](/reference/Symb/IXFLAG_xxx)
---
