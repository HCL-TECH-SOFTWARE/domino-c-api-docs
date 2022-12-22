




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



**Data Type : Standard**



**LNCALLBACK** **-** Calling
convention for callback functions.


**----------------------------------------------------------------------------------------------------------**



**#include
<global.h>**



**Definition :**



#if !defined(OS2)


 


   #define LNCALLBACK
FAR PASCAL


 


#else


 


   /\* OS/2 requires a
separate macro because the ordering of function


      modifiers for
function pointers is different.  This prevents us


      from inserting
\_System in a uniform place (e.g. a replacement


      for PASCAL). \*/


 


   #define LNCALLBACK
\_System


 


#endif


 


**Description :**



Calling
convention for callback functions.


 **Sample Usage :**


/\* C API include files
\*/  

  

#include <global.h>  

#include <nsfdb.h>  

#include <nsfnote.h>  

#include <nsfsearc.h>  

#include <osmem.h>  

#include <nsferr.h>  

  

  

/\* Global data \*/  

  

STATUS result;  

  

/\* Callback function declaration \*/  

  

STATUS LNCALLBACK print\_fields (  

    void         far \* db\_handle,  

    SEARCH\_MATCH far \* search\_info,  

    ITEM\_TABLE   far \* summary\_info)


{  

    . . .  

}  

  

    . . .  

  

/\* Passing address of the callback to Domino or Notes \*/  

  

   result = NSFSearch (  

      db\_handle,      /\* database handle \*/  

      formula\_handle, /\* selection formula \*/  

      NULL,           /\* title of view in selection formula \*/  

      0,              /\* search flags \*/  

      NOTE\_CLASS\_DOCUMENT,/\* note class to find \*/  

      NULL,           /\* starting date (unused) \*/  

      print\_fields,   /\* call function for each note found \*/  

      &db\_handle,     /\* argument to print\_fields \*/  

      NULL);          /\* returned ending date (unused) \*/


 **See Also :**


**[LNCALLBACKPTR](LNCALLBACKPTR.md)**


**[LNPUBLIC](LNPUBLIC.md)**


**[NOTESCALLBACK](NOTESCALLBACK.md)**



----------------------------------------------------------------------------------------------------------


 





