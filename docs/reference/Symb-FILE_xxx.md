##### Symbolic Value : Miscellaneous
##### FILE_xxx - File Types and Search Modifiers for NSFSearch
---
##### #include <osfile.h>
**Description :**
These flags are used with NSFSearch to control what kinds of files are found 
during the search.

When using NSFSearch with search_flags = SEARCH_FILETYPE, you may control the 
search by specifying combinations of FILE_CLASS values in the item_class 
argument to NSFSearch.

The item_class argument to NSFSearch may consists of exactly one file type plus 
zero or more search modifiers.

The file type part of item_class may contain one and only one of the following 
file types:

FILE_ANY
FILE_DBREPL
FILE_DBDESIGN
FILE_MAILBOX
FILE_DBANY
FILE_FTANY
FILE_MDMTYPE
FILE_DIRSONLY
FILE_VPCTYPE
FILE_SRCTYPE
FILE_ANYNOTEFILE
FILE_UNIQUETEMP
FILE_MULTICLN
FILE_SMARTI

Note that item_class may contain one and only one of the above file type 
values. You may not combine different file type values to match multiple file 
name extensions.

The search modifier part of item_class may contain any combination of the 
following search modifiers:

FILE_DIRS
FILE_NOUPDIRS
FILE_RECURSE
FILE_LINKSONLY

You may bitwise-OR any combination of these search modifiers together with one 
of the integer type codes listed previously.

FILE_DIRS causes NSFSearch to call your action routine on subdirectories as 
well as files that match the specified file type.  Since the ".." directory is 
treated as a subdirectory, you may OR in FILE_NOUPDIRS to prevent NSFSearch 
from calling your action routine on the directory "..". FILE_NOUPDIRS has no 
effect unless OR'ed with FILE_DIRS.
 
FILE_RECURSE causes NSFSearch to recursively search subdirectories. 
FILE_RECURSE causes NSFSearch to call your action routine on files that match 
the file type in the directory you opened and in any sub-directory below that.
**Sample Usage :**
```
/* Open the directory. */

 if (error = NSFDbOpen (full_netpath, &dir_handle))
  return (ERR(error));

/* Call NSFSearch to find files in the directory. For each file found, 
call an action routine. */

 if (error = NSFSearch (
  dir_handle,  /* directory handle */
  NULLHANDLE,  /* selection formula */
  NULL,   /* title of view in formula */
  SEARCH_FILETYPE +  /* search for files */
  SEARCH_SUMMARY,  /* return a summary buffer */
  FILE_DBANY +   /* find any .NS? file */
  FILE_DIRS +  /* find subdirectories */
  FILE_NOUPDIRS,   /* don't find the ".." dir */
  NULL,   /* starting date */
  file_action,  /* call for each file found */
  NULL,   /* argument to action routine */
  NULL))   /* returned ending date (unused) */

  {
  NSFDbClose (dir_handle);
  return (ERR(error));
  }

/* Close the directory. */

 if (error = NSFDbClose (dir_handle))
  return (ERR(error));
```
**See Also :**
[NSFSearch](D:/md_files/NSFSearch.md)
---
