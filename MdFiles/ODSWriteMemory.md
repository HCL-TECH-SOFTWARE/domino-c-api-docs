




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Function : Canonical Format
Conversion**



**ODSWriteMemory** **- Convert a
structure from machine-specific format to canonical format.**


**----------------------------------------------------------------------------------------------------------**



**#include <ods.h>**



void
LNPUBLIC **ODSWriteMemory(**  

      void far \*ppDest,  

      WORD  type,  

      const void far \*pSrc,  

      WORD  iterations**);**



**Description :**



This function
converts Domino data structures from machine-specific (host) format to Domino
canonical format.  It writes the result into a memory buffer provided by the
caller.  

  

You must convert data structures to Domino canonical format before appending
them to a note if (1) your API program runs on non-Intel architecture machines,
and (2) your API program is writing a Domino data item of one of the data types
listed below:  

  

    TYPE\_COMPOSITE  

    TYPE\_COLLATION  

    TYPE\_OBJECT  

    TYPE\_VIEW\_FORMAT  

    TYPE\_ICON  

    TYPE\_SIGNATURE  

    TYPE\_SEAL  

    TYPE\_SEALDATA  

    TYPE\_SEAL\_LIST  

    TYPE\_WORKSHEET\_DATA  

    TYPE\_USERDATA


   
TYPE\_QUERY


   
TYPE\_ACTION


   
TYPE\_ASSISTANT\_INFO


   
TYPE\_VIEWMAP\_DATASET


   
TYPE\_VIEWMAP\_LAYOUT


   
TYPE\_CALENDAR\_FORMAT  

  

For example, if your API program runs under UNIX, after initializing a data
structure of type CDPARAGRAPH, you must use ODSWriteMemory() to convert the
structure to Domino canonical format and write the canonical format data to a buffer
before calling NSFItemAppend to append the buffer as an item of TYPE\_COMPOSITE
to a note.  

  

If your API program runs only under Windows, then ODSWriteMemory() is not
necessary, but will do no harm.  Proper use of ODSWriteMemory() makes your code
portable across platforms.  

  

Do not use OSDWriteMemory() for Domino data types other than those listed
above.  Domino and Notes convert non-item data (such as note header data) and
item data of other types to canonical format automatically.


 


**Parameters :**



Input :  

ppDest  -  Address of a void pointer that points to the destination memory
buffer.  ODSWriteMemory writes the canonical form of the Domino structure to
this buffer.  The caller is responsible for ensuring that the specified buffer
has sufficient space to hold the data.  

  

type  -  ODS type - identifies the Domino data structure.  The ODS type symbol
is the underscore character followed by the Domino data structure name. For
example,  \_CDPARAGRAPH identifies a CDPARAGRAPH data structure.  See Symbolic
Value \_xxx (ODS Types) for a list of all valid ODS types.  

  

pSrc  -  Pointer to the Domino data structure in machine-specific (host)
format.  Normally, this is the address of a variable of the type identified by
the type argument. If iterations > 1, pSrc specifies an array of structures
of this type.  

  

iterations  -  Specifies the number of data structures located at the address
specified by pSrc.  

  




Output :  

ppDest  -  After writing the canonical form of the Domino structure to the
buffer, ODSWriteMemory advances the specified void pointer to point to the next
byte after the structure written.  

  




 **Sample Usage :**


  

void               \*pCBuf;  

COLLATION           Collation;  

COLLATE\_DESCRIPTOR  CollateDesc;  

COLLATE\_DESCRIPTOR  CollateDesc2;  

  

/\*   

 \* Initialize pCBuf. Keep pCollationBuffer pointing to the top   

 \* of the buffer, and pCBuf pointing to the next available byte.  

 \*/  

    pCBuf = (void \*)pCollationBuffer;  

  

/\* Initialize the Collation structure. \*/  

  

    Collation.Items = 1;  

    Collation.Flags = NIF\_STAT\_NONE;  

    Collation.signature = COLLATION\_SIGNATURE;  

    Collation.BufferSize = wCollationBufLen;  

/\*  

 \* Convert the Collation structure to Domino canonical format and  

 \* store it in the ODS buffer.  

 \*/  

  

    ODSWriteMemory( &pCBuf, \_COLLATION, &Collation, 1 );  

      

/\*  

 \*  Initialize the collation descriptor for the first column. The  

 \*  first column is a category.  

 \*/  

  

    CollateDesc.Flags = 0;     

    CollateDesc.signature = COLLATE\_DESCRIPTOR\_SIGNATURE;  

    CollateDesc.keytype = COLLATE\_TYPE\_CATEGORY;  

    CollateDesc.NameOffset = 0;  

    CollateDesc.NameLength = wItemName\_1\_Len;  

  

/\*  

 \* Convert the collation descriptor for the first column to Domino   

 \* canonical format, and store it in the buffer.  

 \*/  

  

    ODSWriteMemory( &pCBuf, \_COLLATE\_DESCRIPTOR, &CollateDesc, 1 );  

  

/\*  

 \* Initialize the collation descriptor for the second column. The  

 \* second column is sorted.  

 \*/  

  

    CollateDesc2.Flags = 0;  

    CollateDesc2.signature = COLLATE\_DESCRIPTOR\_SIGNATURE;  

    CollateDesc2.keytype = COLLATE\_TYPE\_KEY;  

    CollateDesc2.NameOffset =  wItemName\_1\_Len;  

    CollateDesc2.NameLength = wItemName\_2\_Len;  

  

/\*  

 \* Convert the collation descriptor for the second column to Domino   

 \* canonical format, and store it in the buffer.  

 \*/  

  

    ODSWriteMemory( &pCBuf, \_COLLATE\_DESCRIPTOR, &CollateDesc2, 1 );  

  

/\*  Append the column 1 item name to the buffer. \*/  

      

    memcpy( pCBuf, szItemName\_1, wItemName\_1\_Len );  

    pCBuf += wItemName\_1\_Len;  

  

/\*  Append the column 2 item name to the buffer. \*/  

      

    memcpy( pCBuf, szItemName\_2, wItemName\_2\_Len );  

    pCBuf += wItemName\_2\_Len;  

  

/\*  Now append the $COLLATION item to the note. \*/  

      

    sError = NSFItemAppend( hNote,  

                            ITEM\_SUMMARY,  

                            VIEW\_COLLATION\_ITEM,  

                            sizeof(VIEW\_COLLATION\_ITEM) - 1,  

                            TYPE\_COLLATION,  

                            pCollationBuffer,  

                            (DWORD) wCollationBufLen );  

  

    OSUnlockObject( hCollationBuffer);  

    OSMemFree( hCollationBuffer );


 **See Also :**


**[NSFItemAppend](NSFItemAppend.md)**


**[NSFItemInfo](NSFItemInfo.md)**


**[ODSLength](ODSLength.md)**


**[ODSReadMemory](ODSReadMemory.md)**


**[\_xxx (ODS Types)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/B6624318DA38E8A885255F18007069DE)**



----------------------------------------------------------------------------------------------------------


 





