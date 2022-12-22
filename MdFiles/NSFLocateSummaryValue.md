




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




 


**Function : Item (Field)**



**NSFLocateSummaryValue** **- Get any
item value in a Summary Buffer.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



BOOL
LNPUBLIC **NSFLocateSummaryValue(**  

      const void far \*summary\_buffer\_ptr,  

      const char far \*item\_name,  

      void far \* far \*item\_value\_ptr\_ptr,  

      WORD far \*item\_len\_ptr,  

      WORD far \*item\_type\_ptr**);**



**Description :**



This routine
locates item values in the Summary Buffer of a note.  A Summary Buffer is an
ITEM\_TABLE containing an array of some of the items associated with that note.
Only items that have the ITEM\_SUMMARY flag set can reside in the summary
buffer. Obtain summary buffers by calling functions NIFReadEntries() or
NSFSearch().  

  

Use NSFLocateSummaryValue to obtain item values when you know the item names
and would like to avoid opening the note. NSFLocateSummaryValue is particularly
valuable when performance is a concern because it does not require that you
open the note before reading item values.  

  

Items have the ITEM\_SUMMARY flag set if the ItemFlags argument of NSFItemAppend
specified ITEM\_SUMMARY when the item was added to the note. Note that functions
such as NSFItemSetText and NSFItemSetNumber will set the ITEM\_SUMMARY flag.


  

Summary items can be used in formulas, view columns, and view selection
criteria. If an item is not marked ITEM\_SUMMARY, it cannot be used in a view,
nor will it be returned in the Summary Buffer obtained via  NIFReadEntries() or
NSFSearch().


 


**Parameters :**



Input :  

summary\_buffer\_ptr  -  A pointer to a buffer containing a summary buffer
(ITEM\_TABLE).  

  

item\_name  -  The null-terminated item name whose value you want to obtain.  

  




Output :  

(routine)  -  Returned from this call-  

  

TRUE - Item was found.  

FALSE - Item was NOT found.  

  

  

item\_value\_ptr\_ptr  -  The address of a void pointer in which the address of
the item's value (within the Summary Buffer) will be returned.  

  

item\_len\_ptr  -  The address of a WORD in which the total length of the item's
value will be returned.  

  

item\_type\_ptr  -  The address of a WORD in which the Domino data type of the
requested item will be returned.  

  




 **Sample Usage :**


  

HANDLE     buffer\_handle;  

BYTE     \*summary;  

char     \*szItemName;  

BOOL      Found;  

char     \*item\_value\_ptr;  

WORD      Length, Type;  

  

NIFReadEntries(coll\_handle, &coll\_pos, NAVIGATE\_CURRENT, 0,  

              NAVIGATE\_NEXT, 0xFFFF, READ\_MASK\_SUMMARY,  

              &buffer\_handle,     NULL, NULL, &entries\_found, NULL);  

  

summary = (BYTE \*) OSLockObject (buffer\_handle);  

  

szItemName = "Subject";  

  

Found = NSFLocateSummaryValue(summary,   

                szItemName, &item\_value\_ptr, &Length, &Type);  

  

if (Found)  

{  

    printf ("Found field '%s'\n", szItemName);  

}              

  

OSUnlockObject (buffer\_handle);  

OSMemFree (buffer\_handle)


 **See Also :**


**[NSFGetSummaryValue](NSFGetSummaryValue.md)**


**[NSFItemAppend](NSFItemAppend.md)**


**[NSFSearch](NSFSearch.md)**


**[NIFReadEntries](NIFReadEntries.md)**



----------------------------------------------------------------------------------------------------------


 





