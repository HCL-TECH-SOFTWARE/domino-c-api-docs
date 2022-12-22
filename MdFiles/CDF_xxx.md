




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



**CDF\_xxx** **-** COLLATE\_DESCRIPTOR
- Flags


**----------------------------------------------------------------------------------------------------------**



**#include <nifcoll.h>**


 **Symbolic Values :**      CDF\_S\_descending   -  (Shift) Number of bits to shift to
access the CDF\_M\_descending field.  

  

      CDF\_M\_descending              -  (Mask) True if descending; False if
ascending order (default).  

  

      CDF\_M\_ignoreprefixes         -  If prefix list, then ignore for sorting.  

  

      CDF\_M\_caseinsensitive        -  \* OBSOLETE \* - see
CDF\_M\_caseinsensitive\_in\_v5.  

(Mask) If set, text compares are case-insensitive.  

  

      CDF\_M\_accentinsensitive     -  \* OBSOLETE \* - see
CDF\_M\_accentinsensitive\_in\_v5.  

(Mask) If set, text compares are accent-insensitive.  

  

      CDF\_M\_permuted     -  (Mask) If set, lists are permuted.  

  

      CDF\_M\_permuted\_pairwise   -  (Mask) Qualifier if lists are permuted; if
set, lists are pairwise permuted, otherwise lists are multiply permuted.  

  

      CDF\_M\_flat\_in\_v5    -  (Mask) If set, treat as permuted.  

  

      CDF\_M\_casesensitive\_in\_v5            -  (Mask) If set, text compares are
case-sensitive.  

  

      CDF\_M\_accentsensitive\_in\_v5          -  (Mask) If set, text compares are
accent-sensitive.  

  




**Description :**



Bit field
masks used to access components of the Flags field in the COLLATE\_DESCRIPTOR
structure.


 **See Also :**


**[COLLATE\_DESCRIPTOR](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/00BE00740029007F85255E37006051E3)**



----------------------------------------------------------------------------------------------------------


 





