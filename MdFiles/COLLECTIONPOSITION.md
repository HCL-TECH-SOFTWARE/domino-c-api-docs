




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



**COLLECTIONPOSITION** **-** Index to a
position within a view.


**----------------------------------------------------------------------------------------------------------**



**#include
<nif.h>**



**Definition :**



typedef struct {  

   WORD  Level;   /\* # levels -1 in tumbler (top level = 0)\*/  

   BYTE MinLevel; /\* MINIMUM level that this position \*/  

                  /\* is allowed to be nagivated to. \*/  

                  /\* This is useful to navigate a \*/  

                  /\* subtree using all navigator codes. \*/  

                  /\* This field is IGNORED unless \*/  

                  /\* the NAVIGATE\_MINLEVEL flag is \*/  

                  /\* enabled (for backward compatibility) \*/  

   BYTE MaxLevel; /\* MAXIMUM level that this position \*/  

                  /\* is allowed to be nagivated to. \*/  

                  /\* This is useful to navigate a \*/  

                  /\* subtree using all navigator codes. \*/  

                  /\* This field is IGNORED unless \*/  

                  /\* the NAVIGATE\_MAXLEVEL flag is \*/  

                  /\* enabled (for backward compatibility) \*/  

   DWORD Tumbler[MAXTUMBLERLEVELS]; /\* Current tumbler (1.2.3, etc) \*/  

                  /\* (an array of ordinal ranks) \*/  

                  /\* (0th entry = top level) \*/  

                  /\* Actual number of array entries is Level+1 \*/  

} COLLECTIONPOSITION;


 


**Description :**



This
structure is used to specify the hierarchical, index position of an item (or
category) within a View(collection).  

  

Level = (number of levels in tumbler - 1)  

  

Tumbler is an array of ordinal ranks within the view; with the first (0) entry
referring to the top level.  

  

For example, consider the following non-Domino Outline Scheme :  

  

I.  First Main Category  

        A.  First sub-category under I  

        B.  Second sub-category under I  

II.  Second Main Category  

        A.  First sub-category under II  

            1.  First item under  II.A  

            2.  Second item under II.A  

        B.  Second sub-category under II  

        C.  Third sub-category under II  

III.  Third Main Category  

  

With this example, [2; II.A.2] refers to the "Second item under
II.A."  

Similarly, [0; III] refers to the "Third Main Category."  

  

Finally, it should be noted that [2; I.B.1], [1; I.C], and [3; II.A.1] are all
NOT valid positions.  

  

[2; I.B.1] because the "Second sub-category under I" has no items.  

[1; I.C] because there is no "Third sub-category under I", and  

[3; II.A.1] because the value of Level (3) shows four levels  

should be represented in the Tumbler and there are only three.  

  




 **See Also :**


**[NIFFindByKey](NIFFindByKey.md)**


**[NIFFindByName](NIFFindByName.md)**


**[NIFReadEntries](NIFReadEntries.md)**



----------------------------------------------------------------------------------------------------------


 





