




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




 


**Data Type : Views**



**COLLATION** **-** Defines
sorting information for the columns in a view note.


**----------------------------------------------------------------------------------------------------------**



**#include
<nifcoll.h>**



**Definition :**



typedef struct {  

   USHORT BufferSize;  /\* Size of entire buffer in bytes \*/  

   USHORT Items;       /\* Number of items following \*/  

   BYTE   Flags;       /\* See COLLATION\_FLAG\_xxx \*/  

   BYTE   signature;   /\* Must be COLLATION\_SIGNATURE \*/  

/\* COLLATE\_DESCRIPTOR desc[];  \*\* COLLATE\_DESCRIPTORs follow \*/  

/\* char text\_area[];   \*\* followed by variable length text \*/  

} COLLATION;


 


**Description :**



This
structure is used to specify the manner in which data in a view is sorted.  The
COLLATION structure, along with its associated COLLATE\_DESCRIPTOR structures
and character strings, comprise the $Collation item in a view note.  

  

BufferSize = total size in bytes of the $Collation item.  

Items          = number of columns in the view that are sorted or categorized.  

Flags         =  Optional.  May be set to a COLLATION\_FLAG\_xxx value. 
Otherwise, set to 0.  

Signature = COLLATION\_SIGNATURE.  

  

These values are immediately followed by an array of COLLATE\_DESCRIPTOR
structures, one for each sorted column.  The collation descriptor array is
followed by a sequence of packed character strings relevant to those
descriptors.  See the definition of COLLATE\_DESCRIPTOR for more details.  

  




 **See Also :**


**[COLLATE\_DESCRIPTOR](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/00BE00740029007F85255E37006051E3)**


**[COLLATION\_FLAG\_xxx](COLLATION_FLAG_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





