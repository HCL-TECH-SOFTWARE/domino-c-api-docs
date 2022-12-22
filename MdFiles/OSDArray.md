




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




 


**Function : Dynamic Array**



**OSDArray** **- Return a
pointer to the elements in the dynamic array.**


**----------------------------------------------------------------------------------------------------------**



**#include <darray.h>**



<elementtype>
far \* **OSDArray(**  

      DARRAY far \*darray,  

      <any>  elementtype**);**



**Description :**



A Domino
dynamic array has three components - a header structure (DARRAY), an array of
element structures, and storage for packed strings.  This function returns a
pointer to the start of the array of element structures.


 


This
function is currently implemented as a macro.


 


**Parameters :**



Input :  

darray  -  Pointer to the dynamic array.  

  

elementtype  -  Structure name of elements in the dynamic array.  

  




Output :  

(routine)  -  Pointer to the array of elements.  The type of the pointer
depends on the elementtype argument.  

  

  




 **Sample Usage :**


    /\* Structure for
dynamic array elements \*/


typedef
struct {  

        WORD           num;  

        PSTRING key;           /\* Note that the PSTRING structures   \*/  

        PSTRING val;           /\* are at the end!!                   \*/  

} KEY\_LIST\_ENTRY;  

#define KEY\_LIST\_ENTRY\_STRINGS 2      /\* Number of PSTRINGs \*/


 


KEY\_LIST\_ENTRY
far \*pEntry;   /\* Pointer to current entry \*/  

char far \*             pKey;          /\* Pointer to key string \*/  

char far \*             pVal;          /\* Pointer to value string \*/


int                    index;


 


        /\*
Get the address of an entry \*/


pEntry =
&(OSDArray (pArray, KEY\_LIST\_ENTRY)[entryNumber]);


 


        /\*
Get addresses of packed strings \*/


        /\*
These strings do NOT have terminating NUL characters! \*/  

pKey = OSDArrayString (pArray, pEntry->key);  

pVal = OSDArrayString (pArray, pEntry->val);


 


        /\*
Print the contents of the entry \*/


printf
("Entry #%d:\tNumber: %d\tKey: ", index, pEntry->num);  

for (index = 0; index < pEntry->key.StringSize; index++)  

        putchar (pKey[index]);  

printf ("\tValue: ");  

for (index = 0; index < pEntry->val.StringSize; index++)  

        putchar (pVal[index]);  

putchar ('\n');


 


 **See Also :**


**[DARRAY](DARRAY.md)**


**[PSTRING](PSTRING.md)**



----------------------------------------------------------------------------------------------------------


 





