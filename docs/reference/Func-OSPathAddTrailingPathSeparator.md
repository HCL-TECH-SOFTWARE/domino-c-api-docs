##### Function : OS
##### OSPathAddTrailingPathSeparator - Adds a trailing path separator for a given OS path. 
---
##### #include <osfile.h>
STATUS **OSPathAddTrailingPathSeparator(**

	char  *dir,
	WORD  wDirSize);
**Description :**
This API adds a trailing path separator, if the last character in the path is 
not a separator. 
**Parameters :**
Input :
*dir  -  Address of directory specification string (ASCIZ)

wDirSize  -  size of the buffer.

Output :
(routine)  -  On invalid or NULL arguments, returns ERR_MISC_INVALID_ARGS error, on successful conversion returns NOERROR. On all other error returns NOTES Error.  


**Sample Usage :**
```

STATUS error = NOERROR; 
char szDataDir[MAXPATH] = {0};
char szFullPath[MAXPATH] = {0};
char szFullPathManual[MAXPATH]= {0};
/* Appending trailing seprator */
if (error = OSPathAddTrailingPathSeparator(szFullPath, sizeof(szFullPath)-1)) 
/* second parameter must not be greater than the size of the buffer being 
passed in otherwise the api could overwrite the buffer */
{
printf("Error in setting separator");
NotesTerm();
return(1);
} 
```
**See Also :**
[](D:/md_files/.md)
---
