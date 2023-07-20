##### Symbolic Value : Database
##### DBCLASS_xxx - Classes of Domino databases.
---
```
#include <nsfdb.h>
```

**Symbolic Values :**

	DBCLASS_BY_EXTENSION	  -  The type of the database is determined by the filename extension. The extensions and their database classes are .NSX (NSFTESTFILE), .NSF (NOTEFILE), .DSK (DESKTOP), .NCF (NOTECLIPBOARD), .NTF (TEMPLATEFILE), .NSG (GIANTNOTEFILE), .NSH (HUGENOTEFILE), NTD (ONEDOCFILE), NS2 (V2NOTEFILE), NTM (ENCAPSMAILFILE).

	DBCLASS_NSFTESTFILE	  -  A test database.

	DBCLASS_NOTEFILE	  -  A standard Domino database.

	DBCLASS_DESKTOP	  -  A Notes desktop (folders, icons, etc.).

	DBCLASS_NOTECLIPBOARD	  -  A Notes clipboard (used for cutting and pasting).

	DBCLASS_TEMPLATEFILE	  -  A database that contains every type of note (forms, views, ACL, icon, etc.) except data notes.

	DBCLASS_GIANTNOTEFILE	  -  A standard Domino database, with size up to 1 GB. This was used in Notes Release 3 when the size of a previous version of a database had been limited to 200 MB.

	DBCLASS_HUGENOTEFILE	  -  A standard Domino database, with size up to 1 GB. This was used in Notes Release 3 when the size of a previous version of a database had been limited to 300 MB.

	DBCLASS_ONEDOCFILE	  -  One document database with size up to 10MB. Specifically used by alternate mail to create an encapsulated database. Components of the document are further limited in size. It is not recommended that you use this database class with NSFDbCreate. If you do, and you get an error when saving the document, you will need to re-create the database using DBCLASS_NOTEFILE.

	DBCLASS_V2NOTEFILE	  -  Database was created as a Notes Release 2 database.

	DBCLASS_ENCAPSMAILFILE	  -  One document database with size up to 5MB. Specifically used by alternate mail to create an encapsulated database. Components of the document are further limited in size. It is not recommended that you use this database class with NSFDbCreate. If you do, and you get an error when saving the document, you will need to re-create the database using DBCLASS_NOTEFILE.

	DBCLASS_LRGENCAPSMAILFILE	  -  Specifically used by alternate mail. Not recomended for use with NSFDbCreate.

	DBCLASS_V3NOTEFILE	  -  Database was created as a Notes Release 3 database.

	DBCLASS_OBJSTORE	  -  Object store.

	DBCLASS_V3ONEDOCFILE	  -  One document database with size up to 10MB. Specifically used by Notes Release 3 alternate mail to create an encapsulated database. Not recomended for use with NSFDbCreate.

	DBCLASS_V4NOTEFILE	  -  Database was created specifically for Domino and Notes Release 4.

	DBCLASS_V5NOTEFILE	  -  Database was created specifically for Domino and Notes Release 5.

	DBCLASS_V6NOTEFILE	  -  Database was created specifically for Domino and Notes Release Notes/Domino 6.

	DBCLASS_V8NOTEFILE	  -  Database was created specifically for Domino and Notes Release Notes/Domino 8.

	DBCLASS_V85NOTEFILE	  -  Database was created specifically for Domino and Notes Release Notes/Domino 8.5.

	DBCLASS_V9NOTEFILE	  -  Database was created specifically for Domino and Notes Release Notes/Domino 9.

	DBCLASS_MASK	  -  Used to mask out the most significant byte in the DBCLASS_xxx value.

	DBCLASS_VALID_MASK	  -  Used to mask out the least significant byte in the DBCLASS_xxx value.


**Description :**

These symbolic constants define the various classes that can be specified when a database is created.


**See Also :**
[NSFDbCreate](/domino-c-api-docs/reference/Func/NSFDbCreate)
[NSFDbClassGet](/domino-c-api-docs/reference/Func/NSFDbClassGet)
---
