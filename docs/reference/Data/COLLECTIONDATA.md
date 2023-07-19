##### Data Type : Views
##### COLLECTIONDATA - Collection information returned by NIFGetCollectionData()
---
```
#include <nif.h>
```

**Definition :**

typedef struct {
   DWORD DocCount;       /* Total number of documents in the
                            collection */
   DWORD DocTotalSize;   /* Total number of bytes occupied by the
                            document entries in the collection */
   DWORD BTreeLeafNodes; /* Number of B-Tree leaf nodes for this
                            index. */
   WORD  BTreeDepth;     /* Number of B-tree levels for this index. */
   WORD  Spare;          /* Unused */
   DWORD KeyOffset[PERCENTILE_COUNT]; /* Offset of ITEM_VALUE_TABLE
                            for each 10th-percentile key value.
                            A series of ITEM_VALUE_TABLEs follows
                            this structure. */
} COLLECTIONDATA;

**Description :**

The function NIFGetCollectionData() returns a handle to a block of memory containing this structure.<br>
<br>
The fields in this structure are:<br>
<br>
DocCount - The number of actual documents in the collection.  (If there are entries in the collection that do not correspond to actual documents, such as categories, they are not included in this total.)<br>
<br>
DocTotalSize - Total number of bytes occupied by the document entries in the collection.<br>
<br>
BTreeLeafNodes &amp; BTreeDepth - Domino maintains a B-tree index structure for the collection;  these fields give the number of leaf nodes and the depth of the tree structure.<br>
<br>
KeyOffset - Table of offsets to the percentile key values.<br>

<ul><br>
The key values used to index this collection are sorted into percentiles.  The first key and every key that corresponds to one-tenth of the collection are returned in a table that is part of this memory block.  Each key is stored in an ITEM_VALUE_TABLE structure, and the offset to the corresponding ITEM_VALUE_TABLE structure is returned in the KeyOffset array.</ul>

<ul>The offsets in the KeyOffset array are byte offsets from the start of the COLLECTIONDATA structure.  Each offset value is added to the address of the COLLECTIONDATA structure to produce the address of the ITEM_VALUE_TABLE that contains the key value at a certain percentile point in the index. <br>
<br>
The PERCENTILE_0 entry in the KeyOffset table is the first value in the index, and the PERCENTILE_100 entry is the last value in the index.</ul>



**Sample Usage :**
```
	/* To access the 50th-percentile key value: */

	{
	ITEM_VALUE_TABLE *pItemValueTable50;
	COLLECTIONDATA *pCollData;
	HANDLE hCollData;
	HCOLLECTION hCollection;

	/* Assume we called NIFOpenCollection to get a valid collection handle, 
hCollection */

	if (error = NIFGetCollectionData (hCollection, &hCollData))
	 return(error);

	pCollData = OSLock(COLLECTIONDATA, hCollData);

	pItemValueTable50 = ((char *) pCollData) + 
pCollData->KeyOffset[PERCENTILE_50];
	}
```

**See Also :**
[ITEM_VALUE_TABLE](/domino-c-api-docs/reference/Data/ITEM_VALUE_TABLE)
[NIFGetCollectionData](/domino-c-api-docs/reference/Func/NIFGetCollectionData)
[PERCENTILE_COUNT](/domino-c-api-docs/reference/Symb/PERCENTILE_COUNT)
[PERCENTILE_xxx](/domino-c-api-docs/reference/Symb/PERCENTILE_xxx)
---
