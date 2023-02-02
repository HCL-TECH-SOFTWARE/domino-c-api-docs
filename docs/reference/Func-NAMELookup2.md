##### Function : Address Book
##### NAMELookup2 - Look up names in Address Books and get item values
---
##### #include <lookup.h>
STATUS LNPUBLIC **NAMELookup2(**

	const char far *ServerName,
	DWORD  Flags,
	WORD  NumNameSpaces,
	const char far *NameSpaces,
	WORD  NumNames,
	const char far *Names,
	WORD  NumItems,
	const char far *Items,
	DHANDLE far *rethBuffer);
**Description :**
This function is an enhanced 32-bit version of NAMELookup and supports 
returning data greater than 64 KB.  Server Administrators can define how much 
data can be returned in a single call by setting the NAMELOOKUP_MAX_MB variable 
in notes.ini.  For example, NAMELOOKUP_MAX_MB=3 will allow NAMELookup2 to 
return 3 MB of data.  If this variable is not set, the default of 1 MB is 
used.  Increasing the default will result in a performance hit on the server 
returning the data.  The maximum size for the amount of returned data is 
MAXDWORD (approximately 4,000 MB).  

      Note:  Address books refer to both Notes Client Address books, and Domino 
Server Address books known as Domino Directories.

       This routine looks up names in the Address Books. It retrieves item 
values from each document it finds that matches a name. It returns a handle to 
a buffer that contains the values of the items requested. Free the buffer after 
processing the data in it.

Use this routine to efficiently find information stored in the Address books. 
NAMELookup2 is particularly useful for looking up information about a given 
name when you don't know, for example, whether the name corresponds to a person 
or a group, or when you don't know which Address book the name resides in.

NAMELookup2 handles multiple views, multiple names, and multiple items. It 
takes, as input, a list of view names, a list of names, and a list of items. It 
searches each view for each name in all the Address books in use. For each 
document that matches a name, NAMELookup2 reads the requested item values. It 
stores the item values in a buffer, and returns the buffer handle.

NAMELookup2 can be used with categorized (hierarchical) views, but this will 
require some knowledge of the view's hierarchy, since searches will be based on 
the categories in the view.  For example, in the $People view in the Domino 
Directory, the first column is categorized by the first letter of the LastName 
item.  Consequently, performing a lookup on the name "A" in the $People view 
will find all people whose last name begins with the letter "A".  If a view has 
multiple levels of categorization, then NAMELookup2 will find only the 
documents immediately under the category specified in the Names parameter.  For 
example, the $PeopleGroupsHier view is categorized based on an organization's 
hierarchy.  Suppose a company "ABCorp" has users in the "Sales" and "Marketing" 
organizations.  If you search the $PeopleGroupsHier, and specify "ABCorp" in 
the Names parameter, NAMELookup will find all people under the top-level of the 
organizational hierarchy "ABCorp", but not those in the organizational units.  
Likewise, specifying "ABCorp\Sales" in the Names parameter will return all 
members of the /Sales/ABCorp organizational unit only.

The list of Address books in use is derived from the Directory Assistance 
database if the server is configured to have a Directory Assistance database.  
Otherwise this list is derived from the NAMES variable in the notes.ini file 
which defines the list of Address books in use. If notes.ini does not specify a 
NAMES variable, the default is "names.nsf". 

NAMELookup2 searches multiple Address books in the order specified by the 
Directory Assistance database or by the NAMES variable. NAMELookup2 stops 
searching for a given name as soon as it finds a match in one of the Address 
books. Therefore, if a given name appears in multiple  Address books, 
NAMELookup2 only returns information for that name from the first database 
searched that contains a match.

NAMELookup2 reads item values from the document's summary buffer. Therefore, 
NAMELookup2 can only retrieve summary item values. 

NAMELookup2 allocates a memory buffer, fills the buffer with the requested item 
values, and stores a handle to this buffer in rethBuffer. Lock the buffer 
before retrieving information from it. Locate information in this buffer using 
NAMELocateNextMatch2, NAMELocateItem2, and NAMELocateMatchAndItem2. Retrieve 
information from this buffer using NAMEGetTextItem2. Unlock and free the buffer 
after processing the information.

If the ServerName parameter is non-NULL, then the look up process takes place 
on the specified server. In this case, if the server is not configured to have 
a Directory Assistance database, the NAMES variable in the server's notes.ini 
file defines the list of Domino Directories searched. NAMELookup2 searches 
Domino Directory databases resident on the specified server.

	It is important to note that if NameLookup2 is performed and the 
specified server is not available then NameLookup2 automatically fails over to 
another server in the cluster.  The failover continues until an available 
server is found or there is no available server in the cluster.  Therefore, it 
is possible that the information could be retrieved from any server in the 
cluster.

The first time a process calls NAMELookup2, it creates a list of open 
collections from the  Address books identified by either the Directory 
Assistance database or the NAMES variable. It saves this list in memory to 
improve the efficiency of repeated look ups. 

        
**Parameters :**
Input :
ServerName  -  Server where look up is performed. Look in the Domino Directories that reside on, and in use by, this server. Specify NULL to perform the lookup on, and search Address books in use by, the local system.

Flags  -  Flags to control lookup (see NAME_LOOKUP_xxx) for a list of the legal values. Normally 0. 

NumNameSpaces  -  Number of views to search in each Address book.

NameSpaces  -  Address of a series of view names to be searched. Each view name must be a null-terminated LMBCS string. There must be NumNameSpaces view names in the series.

NumNames  -  Number of names being looked up.  This parameter must be greater than 0.  If  Flags specify NAME_LOOKUP_ALL and Names = "", then specify NumNames = 1.

Names  -  Address of series of names to look up. Each name must be a null-terminated LMBCS string. The series must contain NumNames strings.  If the view is categorized, you can look up the names in a specific category by specifying the category name in this parameter (see details above).  Names may = "" if Flags specifies NAME_LOOKUP_ALL and NumNames = 1.  This will return all documents, whether or not the view is categorized.

NumItems  -  Number of items to be returned

Items  -  Address of series of item names to return with each match. Each item name must be a null-terminated LMBCS string. The series must contain NumItems names.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully looked up specified names in Address books

ERR_NO_SUCH_NAMES_BOOK - An Address book does not exist

ERR_NO_SUCH_NAMESPACE - One of the specified views does not exist in any of the Address books.

ERR_NO_NAMES_FILE - Unable to open one of the address book databases.

ERR_xxx - Errors returned by lower level functions. Call OSLoadString to obtain the error string.


rethBuffer  -  receives a handle to a buffer containing name information. Buffer consists of a header followed by a series of data records. The number of data records is equal to the number of views searched times the number of names. Use NAMELocateItem2, NAMEGetTextItem2, etc., to read information in the buffer. Free this buffer after processing the information it contains.

**Sample Usage :**
```
#define USERNAMESSPACE "$Users"
#define NUM_NAME_SPACES 1
#define Names  "Bill Smith\0Ted Jones\0Marketing"
#define NUM_NAMES  3
#define MAIL_LOOKUPITEMS "Domain\0Server\0PublicKey\0Members\0Certificate"
#define NUM_LOOKUPITEMS 5
#define ITEM_DOMAIN   0
#define ITEM_SERVER   1
#define ITEM_PUBLICKEY  2
#define ITEM_MEMBERS  3
#define ITEM_CERTIFICATE 4
 
NumViews = NUM_NAME_SPACES;
 NumNames = NUM_NAMES;       /* 3 names to look up */
 NumItems = NUM_LOOKUPITEMS;
 error = NAMELookup2(pMailServerName,  /* Ptr to mail server name */
    0,     /* Flags - DWORD for NAMELookup2*/
    1,      /* Number of name spaces */
    USERNAMESSPACE,  /* Name of name space (view name) */
    NumNames,    /* # of names */
    Names,    /* Ptr to the names themselves */
    NumItems,    /* # of items desired */
    MAIL_LOOKUPITEMS, /* Ptr to the item names */
    &hLookup);   /*  Handle of returned buffer */
 if (error)
  goto Abort;

 pLookup = OSLockObject(hLookup);

 /* For each name requested, traverse the results for each name */

 for (pName = NULL, i = 0; i < (NumViews*NumNames); i++)
  {
  /* Locate the set of matches for the next name searched for */

  pName = NAMELocateNextName2(pLookup, pName, &NumMatches);

  /* Traverse all matches for this name */

  for (pMatch = NULL, j = 0; j < NumMatches; j++)
   {
   pMatch = NAMELocateNextMatch2(pLookup, pName, pMatch);

   /* Here, handle a simple (non-list) item for this match */

   pDomain = NAMELocateItem2(pMatch, ITEM_DOMAIN, &DataType, &Size);
   if (pDomain == NULL)  /* if item not present in this match */
    continue;    /* go on to next match */

   /* Here, handle a text list or text item (this handles
    both kinds) and traverse all members */

   for (k = 0; ; k++)
    {
    if (NAMEGetTextItem2(pMatch, ITEM_MEMBERS, k, 
        Buffer, sizeof(Buffer)) != NOERROR)
     break;
    }
   }
  }
 OSUnlockObject(hLookup);
OSMemFree(hLookup);

```
**See Also :**
[NAMEGetTextItem2](D:/md_files/NAMEGetTextItem2.md)
[NAMELocateItem2](D:/md_files/NAMELocateItem2.md)
[NAMELocateMatchAndItem2](D:/md_files/NAMELocateMatchAndItem2.md)
[NAMELocateNextMatch2](D:/md_files/NAMELocateNextMatch2.md)
[NAMELocateNextName2](D:/md_files/NAMELocateNextName2.md)
[NAMELookup](D:/md_files/NAMELookup.md)
[NAME_LOOKUP_xxx](D:/md_files/NAME_LOOKUP_xxx.md)
---
