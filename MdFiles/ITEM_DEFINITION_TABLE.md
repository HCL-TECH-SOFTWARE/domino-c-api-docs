




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




 


**Data Type : Item (Field) Information**



**ITEM\_DEFINITION\_TABLE** **-** Database
Item Definition Table


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfdb.h>**



**Definition :**



typedef struct {  

   WORD Length; /\* total length of this buffer \*/  

   WORD Items;  /\* number of items in the table \*/  

/\* now come the ITEM\_DEFINITION structures \*/  

/\* now comes the packed text \*/  

} ITEM\_DEFINITION\_TABLE;


 


**Description :**



This table
contains the definition for all the names and labels defined in a database. 
The Item Definition Table consists of a header, defined by the structure
ITEM\_DEFINITION\_TABLE, an array of ITEM\_DEFINITION entries (one for each item),
and a packed character array (no delimiters or separators) of the names of all
the items.  The fields in the ITEM\_DEFINITION\_TABLE structure are:  

  

        Length        Total size, in bytes, of the Item Definition Table  

        Items          Number of Item Definitions in this table  

  




 **Sample Usage :**


/\*  

 \*         GetItemDef  

 \*  

 \*  Get the entry for an item in the ItemDefTable.  You can  

 \*  access all the items in the table by passing an index of 0  

 \*  through tablePtr->Items - 1.  The data returned consists of  

 \*  a pointer to the ITEM\_DEFINITION and a pointer to the name  

 \*  string.  Note that the name string is NOT null-terminated!  

 \*/  

  

int GetItemDef (  

   ITEM\_DEFINITION\_TABLE far \*tablePtr,  /\* In: table address \*/  

   int             i,                           /\* In: which entry \*/  

   ITEM\_DEFINITION far \* \*itemPtrPtr,    /\* Out: address of item \*/  

   char            far \* \*namePtrPtr     /\* Out: address of name \*/  

) {  

   int             j;  

   int             nameOffset;  

   ITEM\_DEFINITION far \*curItemPtr;  

   char            far \*stringPtr;  

  

    /\* Check table limits \*/  

   if ((0 > i) || (i >= tablePtr->Items))  

    return (-1);  

  

    /\* Get the address of the first ITEM\_DEFINITION \*/  

   curItemPtr = (ITEM\_DEFINITION far \*) (((char far \*) tablePtr)  

    + sizeof (ITEM\_DEFINITION\_TABLE));  

  

    /\* Get the address of the packed name strings array \*/  

   stringPtr = (char far \*) (((char far \*) tablePtr)  

    + sizeof (ITEM\_DEFINITION\_TABLE)  

    + (tablePtr->Items \* sizeof (ITEM\_DEFINITION)));  

      

    /\* Scan the table for the entry and name we need \*/  

   for (j = 0; j < i; j++)  

   {  

    stringPtr += curItemPtr->NameLength;  

    curItemPtr++;  

   }  

      

   \*itemPtrPtr = curItemPtr;  

   \*namePtrPtr = stringPtr;  

      

   return (0);  

}


 **See Also :**


**[ITEM\_DEFINITION](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0589662B342324B585256059004CA5E3)**


**[NSFDbItemDefTable](NSFDbItemDefTable.md)**



----------------------------------------------------------------------------------------------------------


 





