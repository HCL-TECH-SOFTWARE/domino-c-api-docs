##### Function : OS Strings
##### OSLoadString - Load a string from a resource file.
---
```
#include <osmisc.h>
WORD LNPUBLIC OSLoadString(

	HMODULE  hModule,
	STATUS  StringCode,
	char far *retBuffer,
	WORD  BufferLength);
```
**Description :**

OSLoadString loads a string into a buffer, given the resource ID of the string 
and a handle to the module containing the string table.

Use OSLoadString to interpret STATUS error codes returned from C API 
functions.  First use the ERR macro to mask off the high order bits of the 
STATUS code returned by the C API function.  Then pass the result as the 
StringCode input to OSLoadString.  Specify NULLHANDLE as the hModule parameter.

Under operating systems such as Unix that do not support string tables, specify 
NULLHANDLE as the hModule parameter. OSLoadString will search the string tables 
internal to Domino and Notes for a string matching the resource ID specified by 
StringCode.

Under Windows, you may use the hModule parameter to specify a non-Domino or 
non-Notes module, and the StringCode parameter to specify a non-Domino string.  
OSLoadString will search for the string specified by StringCode in the string 
table associated with the specified module first.  If the string is not found, 
it goes on to search the string tables internal to Domino and Notes.

In order for DLLs created with the C API to find modules containing non-Domino 
or non-Notes error strings, the module handle of the string table and the 
non-Domino StringCode must be specified.  Again,  OSLoadString will search for 
the string specified by StringCode in the string table associated with the 
specified module first, then if it is not found, will go on to search the 
string tables internal to Domino and Notes.  This functionality is not 
supported for shared objects under UNIX or for other platforms that do not 
support string tables.

In Domino and Notes, all input and output to the API is in Lotus Multi-Byte 
Character Set (LMBCS) optimized for Group 1 and all resource strings are also 
in LMBCS optimized for Group 1.  OSLoadString does not translate resource 
strings after reading them from disk.  If you need to convert strings from 
LMBCS to or from the native character set, use the C API function, OSTranslate.

**Parameters :**
Input :
hModule  -  Specify the module that has the string table OSLoadString should search first.  Specify NULLHANDLE to cause OSLoadString to search the string tables internal to Domino and Notes.  You must specify NULLHANDLE under Unix or other platforms that do not support string table resources.  If you specify NULLHANDLE, the StringCode input argument should be one of the STATUS error codes defined by Notes.

StringCode  -  Resource ID corresponding to the desired string.  This may be a STATUS code returned by a C API function.

BufferLength  -  Maximum length of returned string, generally sizeof(retBuffer) -1.

Output :
(routine)  -  Length of the returned string, or ZERO if it is not found.


retBuffer  -  The address of a text buffer in which the string associated with the STATUS code is returned.  It is the caller's responsibility to pre-allocate this buffer.


**Sample Usage :**
```
nError = NSFDbOpen (szDBFileNameString, &hNotesDB);

if (nError != NOERROR)
{ 
    OSLoadString(hModule, ERR(nError),
            szErrorString, LINEOTEXT-1);
    MessageBox (GetFocus(), szErrorString,
           "Notes Error", MB_OK);
    goto RETURN;
} 
```
**See Also :**
[OSTranslate](/reference/Func/OSTranslate)
[PKG_xxx [ADDIN]](/reference/Symb/PKG_xxx [ADDIN])
[STATUS](/reference/Data/STATUS)
---
