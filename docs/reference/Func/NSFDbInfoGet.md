##### Function : Database
##### NSFDbInfoGet - Gets the database information buffer.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbInfoGet(

	DBHANDLE  hDB,
	char far *retBuffer);
```
**Description :**

This function gets the database information buffer of a Domino database.  The 
information buffer is a NULL terminated string and consists of one or more of 
the following pieces of information:  database title, categories, class, and 
design class.  Use NSFDbInfoParse to retrieve any one piece of information from 
the buffer.

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

The database title also appears on the Notes Desktop below each database icon.

**Parameters :**
Input :
hDB  -  The handle to the database for which you want information.

Output :
(routine)  -  Return status from this call.  A successful call returns NOERROR.


retBuffer  -   A pointer to a text buffer of length NSF_INFO_SIZE in which the database information is returned as a NULL terminated string.  The text buffer consists of one or more of the following pieces of information:  database title, categories, class, and design class.


**Sample Usage :**
```


   /* Copy the Db title */

   if (error_status = NSFDbInfoGet(db_handle_src, db_info))
       goto Exit;

   if (error_status = NSFDbInfoSet(db_handle_dst, db_info))
       goto Exit;

```
**See Also :**
[NSFDbInfoSet](/domino-c-api-docs/reference/Func/NSFDbInfoSet)
[NSFDbInfoParse](/domino-c-api-docs/reference/Func/NSFDbInfoParse)
---
