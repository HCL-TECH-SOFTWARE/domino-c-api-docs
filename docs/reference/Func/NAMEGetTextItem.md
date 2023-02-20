##### Function : Address Book
##### NAMEGetTextItem - Copy a text item from a lookup buffer into the caller's buffer
---
```
#include <lookup.h>
STATUS LNPUBLIC NAMEGetTextItem(

	void far *pMatch,
	WORD  Item,
	WORD  Member,
	char far *Buffer,
	WORD  BufLen);
```
**Description :**

Note:  Address books refer to both Notes Client Address books, and Domino 
Server Address books know as Domino Directories.

       This routine copies a text item from a NAMELookup buffer into a buffer 
provided by the caller. Use this routine to get a TYPE_TEXT item or one member 
of a TYPE_TEXT_LIST item from a look up buffer. This routine copies the text to 
a buffer provided by the caller, truncates the text if it would exceed the 
specified buffer length, and NULL-terminates the text.

NAMELookup creates a look up buffer containing information about a series of 
names in the Address books. The look up buffer consists of a series of records, 
one record per name. Use NAMELocateNextName to locate the next record in the 
buffer. A record may contain multiple matches for a given name. Use 
NAMELocateNextMatch to locate one match in a record. Specify this match 
location in the pMatch argument to NAMEGetTextItem.

To retrieve one element of a text list, specify the text list member number in 
the "Member" argument. Member numbers are zero based: Member = 0 specifies the 
first member. To loop for all members in a text list, loop until this routine 
returns ERR_NO_MORE_MEMBERS.

Use NAMEGetTextItem to retrieve text items from look up buffers. Use 
NAMELocateItem to obtain the data type of an item if you do not know the data 
type in advance, or to retrieve items of data types other than text or text 
list.

**Parameters :**
Input :
pMatch  -  Location of a match in a look up buffer. Use NAMELocateMatch to obtain this location.

Item  -  Item number = index of the item name in the set specified by the "Items" argument to NAMELookup. Zero specifies the first item. Note: this item number must not be greater than the number of items specified by the "NumItems" argument to NAMELookup.

Member  -  Text list member number. Specify 0 if the item is of TYPE_TEXT. Member numbers are zero based: Member = 0 specifies the first member.

Buffer  -  pointer to a buffer to copy result into

BufLen  -  Length, in bytes, of the buffer. Text is truncated to this length.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully copied Item from buffer.

ERR_NO_SUCH_ITEM - Item was not returned for this match

ERR_NO_MORE_MEMBERS - Member number too large

ERR_UNSUPPORTED_DATATYPE - Item data type neither TYPE_TEXT nor TYPE_TEXT_LIST

ERR_xxx - Errors returned by lower level functions. Call OSLoadString to obtain the error string.


Buffer  -  receives the zero-terminated text string


**Sample Usage :**
```
#define USERNAMESSPACE "$Users"
#define Names   "Bill Smith\0Ted Jones\0Marketing"
#define MAIL_LOOKUPITEMS "Domain\0Server\0PublicKey\0Members\0Certificate"
#define ITEM_DOMAIN   0
#define ITEM_SERVER   1
#define ITEM_PUBLICKEY  2
#define ITEM_MEMBERS  3
#define ITEM_CERTIFICATE 4
 
 NumNames = 3;       /* 3 names to look up */
 NumItems = 5;
 error = NAMELookup(pMailServerName,  /* Ptr to mail server name */
     0,     /* Flags */
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

 for (pName = NULL, i = 0; i < NumNames; i++)
  {
  /* Locate the set of matches for the next name searched for */

  pName = NAMELocateNextName(pLookup, pName, &NumMatches);

  /* Traverse all matches for this name */

  for (pMatch = NULL, j = 0; j < NumMatches; j++)
   {
   pMatch = NAMELocateNextMatch(pLookup, pName, pMatch);

   /* Here, handle a simple (non-list) item for this match */

   pDomain = NAMELocateItem(pMatch, ITEM_DOMAIN, &DataType, &Size);
   if (pDomain == NULL)  /* if item not present in this match */
    continue;    /* go on to next match */

   /* Here, handle a text list or text item (this handles
    both kinds) and traverse all members */

   for (k = 0; ; k++)
    {
    if (NAMEGetTextItem(pMatch, ITEM_MEMBERS, k, 
        Buffer, sizeof(Buffer)) != NOERROR)
     break;
    }
   }
  }
 OSUnlockObject(hLookup);
OSMemFree(hLookup);
```
**See Also :**
[NAMELookup](/reference/Func/NAMELookup)
[NAMELocateNextName](/reference/Func/NAMELocateNextName)
[NAMELocateNextMatch](/reference/Func/NAMELocateNextMatch)
[NAMELocateItem](/reference/Func/NAMELocateItem)
[OSLockObject](/reference/Func/OSLockObject)
---
