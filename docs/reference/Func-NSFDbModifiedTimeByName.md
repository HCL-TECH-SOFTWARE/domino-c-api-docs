##### Function : Database
##### NSFDbModifiedTimeByName - Get a database's data/non-data last modified times by DBName.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDbModifiedTimeByName(**

	char *DbName,
	TIMEDATE *retDataModified,
	TIMEDATE *retNonDataModified);
**Description :**
This function obtains the time/date of the last modified data and non-data 
notes in the specified database.  The same information can also be obtained 
with NSFDbOpenExtended.
**Parameters :**
Input :
DbName  -  A pointer to a Domino database name.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully obtained the database's data and non-data last modified times.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


retDataModified  -  The address of a TIMEDATE structure in which the last modified time/date of the most recently modified data note/document is returned.

retNonDataModified  -  The address of a TIMEDATE structure in which the last modified time/date of the most recently modified non-data note/document is returned.

**Sample Usage :**
```
 /* Get Last modified time/date for data and non-data notes */
TIMEDATE  retDataModified, retNonDataModified;
char       *path_name;   
    if (error = NSFDbModifiedTimeByName(path_name, &retDataModified, 
&retNonDataModified))
    {
  goto Exit;
     
    }
```
**See Also :**
[ConvertTextToTIMEDATE](D:/md_files/ConvertTextToTIMEDATE.md)
[ConvertTIMEDATEToText](D:/md_files/ConvertTIMEDATEToText.md)
[NSFDbOpenExtended](D:/md_files/NSFDbOpenExtended.md)
---
