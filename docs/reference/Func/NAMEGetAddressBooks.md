##### Function : Address Book
##### NAMEGetAddressBooks - Get list of Address books in use locally or Domino Directories on a server
---
```
#include <lookup.h>
STATUS LNPUBLIC NAMEGetAddressBooks(

	const char far *pszServer,
	WORD  wOptions,
	WORD far *pwReturnCount,
	WORD far *pwReturnLength,
	DHANDLE far *phReturn);
```
**Description :**

This function gets the list of Address books in use locally or Domino 
Directories on a server.  It returns the list in a buffer. 

	If a server is specified, and that server is configured to have a 
Directory Assistance database (formerly referred to as the Master Address 
Book), then this function gets the list of Domino Directories (Server Address 
books)  from this database.  In Domino and Notes Releases 4.6.x, it only 
includes Domino Name & Address books and not any of the LDAP directories in the 
list.

	If no server is specified or if no Directory Assistance database is 
configured on the specified server, then this function uses the NAMES variable 
in the notes.ini file to construct the list of Address books.  The NAMES 
variable defines the list of Domino Directories and Address books in use by 
Domino and Notes. If the NAMES variable is missing, the default is 
"NAMES.NSF".  For each name in the NAMES list, NAMEGetAddressBooks checks that 
the database exists. If the databases exists, it adds the database path to the 
return buffer. If no named databases exists, NAMEGetAddressBooks sets the 
return count to 0 and returns NOERROR.

If NAMEGetAddressBooks returns NOERROR, and the return count is not 0, then the 
buffer specified by phReturn contains a handle to a return buffer. Call OSLock 
to get a pointer to this buffer.  The return buffer contains a series of 
zero-terminated strings, one after another;  the contents depend on the 
wOptions flag as described below. Call OSUnlock to release the lock and 
OSMemFree to free the buffer specified by this handle after processing the 
information.

If wOptions is 0, each zero-terminated string contains the path to a Address 
database file. This database path is specified relative to the data directory, 
and may contain the port and server name qualifiers.  For each entry in the 
buffer, call OSPathNetParse to obtain the port, server, and file name elements 
of the path (a null string is returned for elements not present in the path).

If wOptions specifies NAME_GET_AB_TITLES, NAMEGetAddressBooks adds the title of 
the database to each entry in the buffer. In this case, each entry in the 
buffer consists of two strings: the path followed by the title.

If wOptions specifies NAME_GET_AB_TITLES bitwise-ored with NAME_DEFAULT_TITLES, 
then if the database has no title, NAMEGetAddressBooks adds the database path 
to the return buffer in place of the title.

**Parameters :**
Input :
pszServer  -  Name of server. Specify NULL to get the list of Address books used on the local system.

wOptions  -  Options (see NAME_xxx). Specify 0 to get just the database paths.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully obtained list of Address books.

ERR_xxx - Errors returned by lower level functions. Call OSLoadString to obtain the error string.


pwReturnCount  -  Number of entries returned   Specifies the number of entries in the return buffer. 

pwReturnLength  -  Length of return buffer

phReturn  -  Return buffer handle. Zero if buffer not allocated. If nonzero, free the buffer specified by this handle after processing the information.


**Sample Usage :**
```
PCHAR   szServer;
PCHAR   szOptions;
WORD    wOption;
STATUS  error;
WORD    wCount;
WORD    wLength;
WORD    wEntry;
WORD    wEntryLen;
DHANDLE  hReturn;
char   *pszReturn;    
char    achPort[MAXPATH];
char    achServer[MAXPATH];
char    achFile[MAXPATH];

szServer = argv[1];
szOptions = argv[2];

if (!strcmp(szOptions,"TITLES"))
{            
    wOption = NAME_GET_AB_TITLES | NAME_DEFAULT_TITLES ;
}
else   
{
    wOption = 0;
}

error = NAMEGetAddressBooks( 
                szServer,
                wOption,
               &wCount,
               &wLength,
               &hReturn);

if (error) return(ERR(error));


/* If there are no entries, return. */

if (!wCount) 
{
    printf ("No entries in NAMES.\n");
   return NOERROR;
}

/* Lock the return buffer. */
pszReturn = OSLock(char, hReturn);

/* Loop through the entries. */

for (wEntry = 0; wEntry < wCount; wEntry++)
{
    /* Get path length. */
    wEntryLen = strlen(pszReturn);

    /* Parse the path into components. */
    OSPathNetParse(pszReturn, achPort, achServer, achFile);

    /* process components */
    printf("Entry %d\n\tPort = %s\n\tServer = %s\n\tFile = %s\n",
            (wEntry+1), achPort, achServer, achFile);

    if (wOption & NAME_GET_AB_TITLES)
    {
        /* Advance to title. */
        pszReturn += wEntryLen+1;
        wEntryLen = strlen(pszReturn);
        printf ("\tTitle = '%s'\n", pszReturn);
    }
        
    /* Advance pointer to next entry. */
    pszReturn += wEntryLen+1;
}

/* Unlock and free the return buffer. */
OSUnlock(hReturn);
OSMemFree(hReturn);
```
**See Also :**
[NAME_xxx](/reference/Symb/NAME_xxx)
---
