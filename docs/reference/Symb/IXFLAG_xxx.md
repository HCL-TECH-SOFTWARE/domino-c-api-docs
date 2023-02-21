##### Symbolic Value : Import/Export
##### IXFLAG_xxx - Flags passed to all file import/export libraries
---
```
#include <ixport.h>
```
**Description :**

These values are passed to the main entry point of all import/export libraries 
in the Flags parameter (second argument). Use these flags to modify the 
behavior of the import or export library when importing or exporting multiple 
files in one step.

An edit-level import library that imports multiple files in one step normally 
creates the output file if IXFLAG_FIRST is set, but if IXFLAG_FIRST is not set, 
it normally opens the existing output file and seeks to the end.

An edit-level export libraray normally opens the specified output file and 
seeks to the end if the output file already exists and the flag IXFLAG_APPEND 
is set. Otherwise, it may create the output file.

A view-level import library may query the user for settings via a dialog box if 
IXFLAG_FIRST is set. The import library may allocate a buffer to save these 
settings, then subsequently use the saved settings if IXFLAG_FIRST is not set. 
When IXFLAG_LAST is set, the library may free the buffer used to save the 
settings.

**Sample Usage :**
```
STATUS LNPUBLIC  MainEntryPoint(EDITIMPORTDATA *EditorData,
                                   WORD Flags,
                                   HMODULE hModule,
                                   char *AltLibraryName,
                                   char *FileName)
{
    STATUS          error, rerror;
    HANDLE          hCompound;  /* handle to Compound Text context */
    COMPOUNDSTYLE   Style;
    DWORD           dwStyleID;
    int             hInputFile, hOutputFile, hCDTextFile;
    HANDLE          hReturnCD;
    DWORD           dwReturnCDLen;
    WORD            wRead;
    char            achReturnCDFileName[MAXPATH];
    char           *pCDText;

    /* If processing the first input file, create the output file. */

    if (Flags & IXFLAG_FIRST)
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
    /* Else output file already exists. Open and seek to the end.*/

        if (error = IeditFileOpenForWrite( EditorData->OutputFileName,
                                    &hOutputFile ))
        {
            IeditMessageBox ("Unable to open temporary file", error);
            goto Exit0;
        }
    
```
**See Also :**
[IXENTRYPROC](/domino-c-api-docs/reference/Data/IXENTRYPROC)
[EDITEXPORTDATA](/domino-c-api-docs/reference/Data/EDITEXPORTDATA)
[EDITIMPORTDATA](/domino-c-api-docs/reference/Data/EDITIMPORTDATA)
---
