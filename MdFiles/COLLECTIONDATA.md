




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
 /\* Style Definitions \*/
 p.MsoNormal, li.MsoNormal, div.MsoNormal
 {margin-top:0cm;
 margin-right:0cm;
 margin-bottom:8.0pt;
 margin-left:0cm;
 line-height:107%;
 font-size:11.0pt;
 font-family:"Calibri",sans-serif;}
.MsoChpDefault
 {font-size:11.0pt;}
.MsoPapDefault
 {margin-bottom:8.0pt;
 line-height:107%;}
 /\* Page Definitions \*/
 @page WordSection1
 {size:612.0pt 792.0pt;
 margin:72.0pt 72.0pt 72.0pt 72.0pt;}
div.WordSection1
 {page:WordSection1;}
-->




**Initial Release 4.0**



**Data Type : Views**



**COLLECTIONDATA** **-** Collection
information returned by NIFGetCollectionData()


**----------------------------------------------------------------------------------------------------------**



**#include
<nif.h>**



**Definition :**



typedef struct {  

   DWORD DocCount;       /\* Total number of documents in the  

                            collection \*/  

   DWORD DocTotalSize;   /\* Total number of bytes occupied by the  

                            document entries in the collection \*/  

   DWORD BTreeLeafNodes; /\* Number of B-Tree leaf nodes for this  

                            index. \*/  

   WORD  BTreeDepth;     /\* Number of B-tree levels for this index. \*/  

   WORD  Spare;          /\* Unused \*/  

   DWORD KeyOffset[PERCENTILE\_COUNT]; /\* Offset of ITEM\_VALUE\_TABLE  

                            for each 10th-percentile key value.  

                            A series of ITEM\_VALUE\_TABLEs follows  

                            this structure. \*/  

} COLLECTIONDATA;


 


**Description :**



The function
NIFGetCollectionData() returns a handle to a block of memory containing this
structure.  

  

The fields in this structure are:  

  

DocCount - The number of actual documents in the collection.  (If there are
entries in the collection that do not correspond to actual documents, such as
categories, they are not included in this total.)  

  

DocTotalSize - Total number of bytes occupied by the document entries in the
collection.  

  

BTreeLeafNodes & BTreeDepth - Domino maintains a B-tree index structure for
the collection;  these fields give the number of leaf nodes and the depth of
the tree structure.  

  

KeyOffset - Table of offsets to the percentile key values.  

  




The key
values used to index this collection are sorted into percentiles.  The first
key and every key that corresponds to one-tenth of the collection are returned
in a table that is part of this memory block.  Each key is stored in an ITEM\_VALUE\_TABLE
structure, and the offset to the corresponding ITEM\_VALUE\_TABLE structure is
returned in the KeyOffset array.


 


The offsets in the KeyOffset array are byte offsets from the start
of the COLLECTIONDATA structure.  Each offset value is added to the address of
the COLLECTIONDATA structure to produce the address of the ITEM\_VALUE\_TABLE
that contains the key value at a certain percentile point in the index. 


 


The PERCENTILE\_0 entry in the KeyOffset table is the first value
in the index, and the PERCENTILE\_100 entry is the last value in the index.


 


 **Sample Usage :**


   /\* To access the
50th-percentile key value: \*/


 


      {


      ITEM\_VALUE\_TABLE
\*pItemValueTable50;


      COLLECTIONDATA \*pCollData;


      HANDLE hCollData;


      HCOLLECTION hCollection;


 


      /\* Assume we called
NIFOpenCollection to get a valid collection handle, hCollection \*/


 


       if (error = NIFGetCollectionData
(hCollection, &hCollData))


             return(error);


 


      pCollData =
OSLock(COLLECTIONDATA, hCollData);


 


      pItemValueTable50 = ((char \*)
pCollData) + pCollData->KeyOffset[PERCENTILE\_50];


      }


 **See Also :**


**[ITEM\_VALUE\_TABLE](ITEM_VALUE_TABLE.md)**


**[NIFGetCollectionData](NIFGetCollectionData.md)**


**[PERCENTILE\_COUNT](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/3071BA559D3650D285256224004558D3)**


**[PERCENTILE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/844C4ED0E0544C0085256224004584CA)**



----------------------------------------------------------------------------------------------------------


 





