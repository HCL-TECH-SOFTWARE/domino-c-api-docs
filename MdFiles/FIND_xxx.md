




<!--
 /\* Font Definitions \*/
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




 


**Symbolic Value : Views**



**FIND\_xxx** **-** NIFFindByKey(),
NIFFindByName() - FindFlags


**----------------------------------------------------------------------------------------------------------**



**#include <nif.h>**


 **Symbolic Values :**      FIND\_PARTIAL        -  Match only the initial characters
("T" matches "Tim", "i" does not match
"Tim"). If multiple keys are used, a partial match is done on each of
the keys in the order that they are specified. A partial match must be found
for all specified keys in order for a particular entry to be considered a
successful match.  

  

      FIND\_CASE\_INSENSITIVE   -  Case insensitive matching ("tim"
matches "Tim").  

  

      FIND\_RETURN\_DWORD      -  Return up to MAXDWORD number of matching notes.
If not specified, return up to MAXWORD number of matching notes.  

  

      FIND\_ACCENT\_INSENTIVE             -  Search disregards diacritical marks.  

  

      FIND\_UPDATE\_IF\_NOT\_FOUND     -  If key is not found, update collection
and search again.  

  

      FIND\_LESS\_THAN   -  Find last entry less than the key value. (Specify no
more than one of: FIND\_LESS\_THAN, FIND\_FIRST\_EQUAL, FIND\_LAST\_EQUAL,
FIND\_GREATER\_THAN)  

  

      FIND\_FIRST\_EQUAL            -  Find first entry equal to the key value
(if more than one). This flag is the default. (Specify no more than one of:
FIND\_LESS\_THAN, FIND\_FIRST\_EQUAL, FIND\_LAST\_EQUAL, FIND\_GREATER\_THAN)  

  

      FIND\_LAST\_EQUAL             -  Find last entry equal to the key value (if
more than one). (Specify no more than one of: FIND\_LESS\_THAN, FIND\_FIRST\_EQUAL,
FIND\_LAST\_EQUAL, FIND\_GREATER\_THAN)  

  

      FIND\_GREATER\_THAN       -  Find first entry greater than the key value.
(Specify no more than one of: FIND\_LESS\_THAN, FIND\_FIRST\_EQUAL, FIND\_LAST\_EQUAL,
FIND\_GREATER\_THAN)  

  

      FIND\_EQUAL           -  Qualifies LESS\_THAN and GREATER\_THAN to mean
LESS\_THAN\_OR\_EQUAL and GREATER\_THAN\_OR\_EQUAL  

  

      FIND\_COMPARE\_MASK      -  Bitmask of FIND\_LESS\_THAN, FIND\_FIRST\_EQUAL,
FIND\_LAST\_EQUAL, FIND\_GREATER\_THAN, FIND\_EQUAL comparison flags.  

  

      FIND\_RANGE\_OVERLAP     -  Overlapping ranges match, and values within a
range match. This symbol is valid for fields of type TYPE\_TIME\_RANGE and
TYPE\_NUMBER\_RANGE. Therefore it should only be used with NIFFindByKey.  

  

      FIND\_RETURN\_ANY\_NON\_CATEGORY\_MATCH    -  Return any entry representing an
actual document (a non-category entry), instead of searching for the first (or
last) entry in the category. It is unpredictable exactly which entry you will
get. A count of the matched document and any subsequent documents that match is
returned. This count may be less than the actual number of documents that
match.  

  

      FIND\_NONCATEGORY\_ONLY         -  Only match non-category entries.  

  




**Description :**



These flags
are used by NIFFindByKey and NIFFindByName to control how the view is searched
for the key. The flags,  FIND\_PARTIAL, FIND\_CASE\_INSENSITIVE, and
FIND\_ACCENT\_INSENSITIVE should only be used for character data, since a
"partial number" or "partial date" is not well defined.  


 


The
FIND\_LESS\_THAN and FIND\_GREATER\_THAN flags refer to the way the sorted column
keys are ordered and displayed, not the way they compare with each other.
FIND\_LESS\_THAN means "find the entry before" and FIND\_GREATER\_THAN
means "find the entry after" a desired key.  The FIND\_LESS\_THAN and
FIND\_GREATER\_THAN flags will result in success if at least one key that is less
than or greater than the specified key, respectively, is found.  


 


If a
FIND\_FIRST\_EQUAL or FIND\_LAST\_EQUAL comparison is specified and the number of
matches is requested to be returned, then the number of entries which match the
specified key will be returned.  If a FIND\_LESS\_THAN or FIND\_GREATER\_THAN
comparison is specified, then the number of matching entries cannot be
requested.


 **See Also :**


**[NIFFindByName](NIFFindByName.md)**


**[NIFFindByKey](NIFFindByKey.md)**



----------------------------------------------------------------------------------------------------------


 





