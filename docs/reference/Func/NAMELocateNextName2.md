##### Function : Address Book
##### NAMELocateNextName2 - Locate the next record in a look up buffer
---
```
#include <lookup.h>
void far * LNPUBLIC NAMELocateNextName2(

	void far *pLookup,
	void far *pName,
	DWORD far *retNumMatches);
```
**Description :**

This function is an enhanced 32-bit version of NAMELocateNextName. 

       This routine finds the next record in a look up buffer. A look up buffer 
is created by a call to NAMELookup2. A look up buffer contains a series of 
records. Each record contains information about one name from one view in an 
Address book or Domino Directory (Server's Address book).

The number of records in a look up buffer is equal to the number of views 
searched times the number of names looked up. Each record may contain multiple 
matches for the given name if multiple documents in the view match the name. 
NAMELocateNextName2 finds the next record (or the first record) in the buffer 
and returns the name itself and the number of matches in the record.

Use this function to find the next record in a buffer created by NAMELookup2, 
and to determine how many matches NAMELookup2 found for that name in that view.

Call NAMELocateNextName2 in a loop to process each record in the buffer created 
by NAMELookup2. Specifying pName = NULL on the first iteration to get the 
record for the first match. and the value returned from NAMELocateNextName2 on 
each subsequent iteration. Execute the loop for each record in the buffer.


**Parameters :**
Input :
pLookup  -  Address of a look up buffer containing information returned from NAMELookup2. NAMELookup2 returns a handle. Call OSLockObject on the handle to obtain this address.

pName  -  Previous record in the buffer. Specify NULL to locate the first record in the buffer.

Output :
(routine)  -  The next record in the look up buffer. If pName is NULL on input, then this returns the first record in the buffer. If pName specifies the last record in the buffer, then this returns NULL.


retNumMatches  -  Receives the number of matches in the next record. If NAMELookup2 finds more than one match for a given name in a given view, then the record corresponding to that name in that view contains more than one match.


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
    0,     /* Flags - DWORD */
    1,      /* Number of name spaces */
    USERNAMESSPACE,  /* Name of name space (view name) */
    NumNames,    /* # of names */
    Names,    /* Ptr to the names themselves */
    NumItems, 	  /* # of items desired */
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
[NAMEGetTextItem2](/domino-c-api-docs/reference/Func/NAMEGetTextItem2)
[NAMELocateItem2](/domino-c-api-docs/reference/Func/NAMELocateItem2)
[NAMELocateNextMatch2](/domino-c-api-docs/reference/Func/NAMELocateNextMatch2)
[NAMELocateNextName](/domino-c-api-docs/reference/Func/NAMELocateNextName)
[NAMELookup2](/domino-c-api-docs/reference/Func/NAMELookup2)
[OSLockObject](/domino-c-api-docs/reference/Func/OSLockObject)
---
