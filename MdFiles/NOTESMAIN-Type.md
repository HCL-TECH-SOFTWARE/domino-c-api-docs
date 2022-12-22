




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




 


**Data Type : Mixed 32/16-bit Model**



**NOTESMAIN** **-** \* OBSOLETE \*
Calling convention for NotesMain and AddInMain


**----------------------------------------------------------------------------------------------------------**



**#include
<global.h>**



**Definition :**



#define NOTESMAIN
LNPUBLIC


 


**Description :**



\*\*\*OBSOLETE
- Included for backward compatibility only\*\*\*


 


This macro
defines the calling convention used for NotesMain and AddInMain programs.  In
the mixed 32/16-bit model for OS/2 2.1, this macro will define NotesMain or
AddInMain to be a 32-bit program using the "\_Optlink" calling
convention.  Under Windows and OS/2 1.x, the calling convention used is
"FAR PASCAL".  On other platforms, this macro is null;  no special
calling convention is used.


 **Sample Usage :**


STATUS NOTESMAIN
NotesMain (int argc, char \* argv[])  

{  

    /\* Here's the main module \*/  

}


 **See Also :**


**[AddInMain](AddInMain.md)**


**[LNPUBLIC](LNPUBLIC.md)**


**[NOTESAPI](NOTESAPI.md)**


**[NOTESAPICDECL](NOTESAPICDECL.md)**


**[NOTESCALLBACK](NOTESCALLBACK.md)**


**[NotesMain](NotesMain.md)**



----------------------------------------------------------------------------------------------------------


 





