##### Function : Database
##### NSFDbInfoSet - Sets the database information buffer.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbInfoSet(

	DBHANDLE  hDB,
	char far *Buffer);
```
**Description :**

This function sets the database information buffer in a Domino database.  The 
information buffer is a character array that is NSF_INFO_SIZE bytes and 
consists of one or more of the following pieces of information: database title, 
categories, class, and design class. You can use NSFDbInfoGet to first get the 
database information buffer, then use NSFDbInfoModify to change any one piece 
of information in the database information buffer, and then use NSFDbInfoSet to 
store the modified database information buffer in the database.    

Database information appears in the Notes UI, in the File, Database, Properties 
InfoBox.  Clicking the Basics tab displays the Title field with the database 
title.  Selecting the Design tab opens the Design tabbed page. The database 
class is displayed in the Database is a template/Template Name field and the 
database design class is displayed in the Inherit design from template/Template 
Name field. The Categories field displays the database categories.  Database 
categories are different than view categories.  Database categories are 
keywords specified for the database.  Each server's database catalog 
(CATALOG.NSF) contains a view, called Databases by Category, which lists only 
the categorized databases.

**Parameters :**
Input :
hDB  -  The handle to the database for which you want to set the database information buffer.

Buffer  -  A pointer to a text buffer of length NSF_INFO_SIZE.  The text buffer consists of one or more of the following pieces of information:  database title, categories, class, and design class.

Output :
(routine)  -  Return status from this call -- indicates either sucess or what the error is.  The return codes include:

NOERROR
ERR_NSF_INFO_SIZE
ERR_NOACCESS



**Sample Usage :**
```

   /* Copy the Db tile */

   if (error_status = NSFDbInfoGet(db_handle_src, db_info))
       goto Exit;
   if (error_status = NSFDbInfoSet(db_handle_dst, db_info))
       goto Exit;

```
**See Also :**
[NSFDbInfoGet](/reference/Func/NSFDbInfoGet)
[NSFDbInfoModify](/reference/Func/NSFDbInfoModify)
---
