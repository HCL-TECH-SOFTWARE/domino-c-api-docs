




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




 


**Function : Formula**



**NSFTranslateSpecial** **- Translate
@Function Escape Sequences**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdata.h>**



STATUS
LNPUBLIC **NSFTranslateSpecial(**  

      void far \*InputString,  

      WORD  InputStringLength,  

      void far \*OutputString,  

      WORD  OutputStringBufferLength,  

      NOTEID  NoteID,  

      void far \*IndexPosition,  

      INDEXSPECIALINFO far \*IndexInfo,  

      DHANDLE  hUnreadList,  

      DHANDLE  hCollapsedList,  

      char far \*FileTitle,  

      char far \*ViewTitle,  

      WORD far \*retLength**);**



**Description :**



Some
@Functions cannot be translated when the formula is evaluated.  Instead, the
value must be obtained when the result is to be displayed or used.  These
functions place a special escape sequence in the result string where the actual
values is to be placed.  The routine NSFTranslateSpecial() substitutes the
actual values for the escape sequence.  

  

@Functions which generate these escape sequences are:  

  

        @DocNumber  

        @DocSiblings  

        @DocChildren  

        @DocDescendants  

        @IsExpandable  

        @DocLevel  

        @IsCategory  

        @DocParentNumber  

  




 


**Parameters :**



Input :  

InputString  -  Address of the input string to be translated.  

  

InputStringLength  -  Length of the input string.  

  

OutputStringBufferLength  -  Size of the output string buffer.  

  

NoteID  -  ID of the note being translated.  

  

IndexPosition  -  Address of a COLLECTIONPOSITION containing the index
position.  

  

IndexInfo  -  Address of an INDEXSPECIALINFO containing miscellaneous index
information.  

  

hUnreadList  -  Handle of the "Unread" note ID list.  

  

hCollapsedList  -  Handle of the "Collapsed" note ID list.  

  

FileTitle  -  Address of the null-terminated notefile title string.  

  

ViewTitle  -  Address of the null-terminated view title string.  

  




Output :  

(routine)  -  Return status from this call -- indicates either sucess or what
the error is. The return codes include:  

  

NOERROR - Operation succeeded.  

  

  

OutputString  -  Address of the output string buffer.  

  

retLength  -  Length of the output string  

  




 **See Also :**


**[INDEXSPECIALINFO](INDEXSPECIALINFO.md)**



----------------------------------------------------------------------------------------------------------


 





