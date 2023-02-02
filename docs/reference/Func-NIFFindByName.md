##### Function : Views
##### NIFFindByName - Finds notes using the collection's primary sort key.
---
##### #include <nif.h>
STATUS LNPUBLIC **NIFFindByName(**

	HCOLLECTION  hCollection,
	const char far *Name,
	WORD  FindFlags,
	COLLECTIONPOSITION far *retIndexPos,
	DWORD far *retNumMatches);
**Description :**
This function searches through a collection for notes whose primary sort key 
matches a given string. The primary sort key for a given note is the value 
displayed for that note in the leftmost sorted column in the view or folder. 
Use this function only when the leftmost sorted column of the view or folder is 
a string.

This function yields the COLLECTIONPOSITION of the first note in the collection 
that matches the string. It also yields a count of the number of notes that 
match the string.  With views that are not categorized, all notes with primary 
sort keys that match the string appear contiguously in the view or folder.  
This means you may pass the resulting COLLECTIONPOSITION and match count as 
inputs to NIFReadEntries to read all the entries in the collection that match 
the string.

This routine returns limited results if the view is categorized.  Views that 
are categorized do not necessarily list all notes whose sort keys match the 
string contiguously; such as in the case where the category note intervenes. 
Likewise, this routine cannot be used to locate notes that are categorized 
under multiple categories (the resulting position is unpredictable), and also 
cannot be used to locate responses.

Use NIFFindByKey if the leftmost sorted column is a number or a time/date.

Returning the number of matches on an inequality search is not supported.  In 
other words, if you specify any one of the following for the FindFlags argument:
	FIND_LESS_THAN
	FIND_LESS_THAN | FIND_EQUAL
	FIND_GREATER_THAN
	FIND_GREATER_THAN | FIND_EQUAL
this function cannot determine the number of notes that match the search 
condition.  In this case you may want to specify NULL for the retNumMatches 
argument.  If you do not specify NULL for the retNumMatches argument, then 
*retNumMatches will be set to 1.
**Parameters :**
Input :
hCollection  -  The handle of the collection you want to search.

Name  -  A pointer to a null-terminated LMBCS string. The function will look for notes (within the collection) whose primary sort key matches this string.

FindFlags  -  Flags that control the comparison rules used when Name is compared to the notes in the collection. The find flags are described in FIND_xxx, and may be or'ed together to combine functionailty.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_NOT_FOUND


retIndexPos  -  A pointer to a COLLECTIONPOSITION that receives the place within the collection where the match is found.  If more than one matching note was found, the position of the first matching note will be returned.  You can use retIndexPos with NIFReadEntries to get the notes found by this search.

retNumMatches  -  The address of a DWORD in which the number of matching entries is returned.  This value is usually passed-on to a subsequent call to NIFReadEntries().  It can also be used simply to determine if the name has multiple matches or not (ambiguity).

The number of matching entries is not supported if FIND_LESS_THAN, FIND_LESS_THAN | FIND_EQUAL, FIND_GREATER_THAN, or FIND_GREATER_THAN | FIND_EQUAL is specified in the FindFlags argument.  In this case, you may specify NULL for the retNumMatches argument.  If you do not specify NULL, then 1 is returned as the number of matching notes.

**Sample Usage :**
```
/* This code fragment shows how to find only those notes
in a collection where the left-hand column of the view is "Jones". 
We assume the view is sorted in ascending order on this column. */

        error = NIFFindByName (
                hCollection,     
                "JONES",      
                FIND_PARTIAL | FIND_CASE_INSENSITIVE, 
                &pCollPosition,      
                &MatchSize);    

        if (ERR(error) == ERR_NOT_FOUND) 
                goto noNotes;
       if (error) 
               return(ERR(error));

        if (error = NIFReadEntries(
                    hCollection, 
                    &pCollPosition,  
                    NAVIGATE_CURRENT,    
                    0,  
                    NAVIGATE_NEXT,    
                    MatchSize,    
                    READ_MASK_NOTEID, 
                    &hBuffer,   
                    NULL,   
                    NULL,   
                    &NumberReturned,   
                    NULL))  
            return(ERR(error));

        if (hBuffer != NULLHANDLE)
        {
        IdList = (NOTEID far *)OSLockObject(hBuffer);

        for (i=0; i<NumberReturned; i++)
            printf ("Note ID number %d is: %lu\n", i+1, IdList[i]);

            OSUnlockObject(hBuffer);
            OSMemFree(hBuffer);
        }

        noNotes: ;

```
**See Also :**
[NIFOpenCollection](D:/md_files/NIFOpenCollection.md)
[NIFReadEntries](D:/md_files/NIFReadEntries.md)
---
