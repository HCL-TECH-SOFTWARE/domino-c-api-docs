




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




 


**Symbolic Value : Field**



**ITEM\_xxx** **-** Flags
attached to an item in a note.


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**


 **Symbolic Values :**      ITEM\_SIGN   -  This item is signed.  

  

      ITEM\_SEAL              -  This item is sealed. When used in
NSFItemAppend, the item is encryption enabled; it can later be encrypted if
edited from the Notes UI and saved in a form that specifies Encryption.  

  

      ITEM\_SUMMARY     -  This item is stored in the note's summary buffer.
Summary items may be used in view columns, selection formulas, and @functions.
Summary items may be accessed via the SEARCH\_MATCH structure provided by
NSFSearch or in the buffer returned by NIFReadEntries. API program may read,
modify, and write items in the summary buffer without opening the note first.
The maximum size of the summary buffer is 32K. Items of TYPE\_COMPOSITE may not
have the ITEM\_SUMMARY flag set.  

  

      ITEM\_READWRITERS         -  This item is an Author Names field as
indicated by the READ/WRITE-ACCESS flag. Item is TYPE\_TEXT or TYPE\_TEXT\_LIST.
Author Names fields have the ITEM\_READWRITERS flag or'd with the ITEM\_NAMES
flag.  

  

      ITEM\_NAMES          -  This item is a Names field. Indicated by the NAMES
(distinguished names) flag. Item is TYPE\_TEXT or TYPE\_TEXT\_LIST.  

  

      ITEM\_PLACEHOLDER         -  This item is a placeholder field in a form
note. Item is TYPE\_INVALID\_OR\_UNKNOWN.  

  

      ITEM\_PROTECTED             -  A user requires editor access to change
this field.  

  

      ITEM\_READERS      -  This is a Reader Names field. Indicated by the
READER-ACCESS flag. Item is TYPE\_TEXT or TYPE\_TEXT\_LIST.  

  

      ITEM\_UNCHANGED             -  Item is same as on-disk.  

  




**Description :**



These flags
define the characteristics of an item (field) in a note.  The flags may be
bitwise or'ed together for combined functionality.


 **Sample Usage :**


    if (error =
NSFItemAppend ( hNote,   

                                ITEM\_SUMMARY | ITEM\_READWRITERS | ITEM\_NAMES,  

                                DISCUSS\_ITEM\_AUTHOR,  /\* "Author" \*/  

                                strlen(DISCUSS\_ITEM\_AUTHOR),  

                                TYPE\_TEXT,  

                                szAuthor,  

                                strlen(szAuthor)))  

    {  

        printf ("Error: unable to append Author field.\n");  

    }


 **See Also :**


**[ITEM\_xxx [NAMES]](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/557B87BE33862F688525623800493995)**


**[ITEM\_xxx [READERS]](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0134426255B7EE1885256238004A727D)**


**[ITEM\_xxx [READWRITERS]](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/C2175B1F1F4585C4852562380049DF01)**


**[NSFItemAppend](NSFItemAppend.md)**


**[TYPE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/002100600028002B85255E2D0079321C)**



----------------------------------------------------------------------------------------------------------


 





