




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




**Initial Release 8.0**



**Data Type : Handles**



**DHANDLE** **-** General
definition for handles used by Domino and Notes after ND8.0.


**----------------------------------------------------------------------------------------------------------**



**#include
<global.h>**



**Definition :**



#if defined(ND64) ||
defined(NDUNIX64)


        /\*
this is defined here for all platforms as this is used somewhere in the pack \*/


        #ifdef
HANDLE\_IS\_64BITS


               #if
defined(UNIX)


                       typedef
unsigned long DHANDLE;        /\* 64-bit HANDLEs \*/


               #else


                       typedef
unsigned long long DHANDLE;   /\* 64-bit HANDLEs on Windows \*/


               #endif


        #else


               typedef
unsigned int DHANDLE; /\* 32-bit HANDLEs \*/


               #ifndef
HANDLE\_IS\_32BITS


                       #define
HANDLE\_IS\_32BITS


               #endif


        #endif


        #if
!defined(WINDOWS\_INCLUDED)


               typedef
unsigned int HANDLE, \*PHANDLE;            /\* for tdanalyzer \*/


        #endif


#else          /\*
32 BIT platforms \*/


        #if
!defined(WINDOWS\_INCLUDED)


               #if
defined(DOSW16)


                       typedef
unsigned int DHANDLE; /\* really a short, but compiler is picky \*/


               #elif
defined(HANDLE\_IS\_32BITS)


                       typedef
unsigned int DHANDLE; /\* 32-bit HANDLEs \*/


               #else


                       typedef
unsigned short DHANDLE;


               #endif


               typedef
DHANDLE HANDLE, \*PHANDLE;


        #else


               typedef
HANDLE DHANDLE;


        #endif


#endif


 


**Description :**



This
datatype is the base type for various kinds of handles used by Domino and
Notes. After ND8.0, DHANDLE will be used instead of HANDLE.


 




----------------------------------------------------------------------------------------------------------


 





