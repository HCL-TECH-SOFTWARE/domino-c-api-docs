




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




**Initial Release 5.0.1**



**Function : Edit Fax**



**EditorAppendBitmapToNote** **- An
Editfax API - appending a FAX bitmap to a note.**


**----------------------------------------------------------------------------------------------------------**



**#include <editfax.h>**



STATUS
far PASCAL **EditorAppendBitmapToNote(**  

      HBITMAP  hBitmap,  

      WORD  cxPaperTwips,  

      WORD  cyPaperTwips,  

      WORD  DisplayScalingPercent,  

      NOTEHANDLE  hNote,  

      WORD  ItemFlags,  

      char \*ItemName,  

      WORD  ItemNameLength,  

      void \*ParagraphAttributes**);**



**Description :**



This API is
supported in the Intel Windows 32-bit environment only.


 


This Editfax
API appends a FAX bitmap to a specified item in a specified note.  


 


**Parameters :**



Input :  

hBitmap  -  Handle to a FAX bitmap.  

  

cxPaperTwips  -  Width of the paper, in TWIPS.  

  

cyPaperTwips  -  Height of the paper, in TWIPS.  

  

DisplayScalingPercent  -  The scaling factor to be used when appending the
bitmap to the note.  100 indicates retaining the original bitmap size.  

  

hNote  -  Handle of the note the FAX bitmap will be appended to.  

  

ItemFlags  -  These flags are defined in ITEM\_xxx.  

  

ItemName  -  Name of the rich text item the FAX bitmap will be appended to.  

  

ItemNameLength  -  Length of the "ItemName".  

  

ParagraphAttributes  -  The format of the rich-text paragraph.  See
CDPABDEFINITION for the format structure.  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  




 **Sample Usage :**



  .


  .


  .


 


if
(PageNumber > 1)     /\* add a paragraph \*/


   {


     
memset(&Pab, 0, sizeof(CDPABDEFINITION));


     
Pab.Flags      = PABFLAG\_PAGINATE\_BEFORE | PABFLAG\_PROPAGATE;


     
Pab.LeftMargin = Pab.FirstLineLeftMargin = ONEINCH;


     
Pab.PABID      = 0xffff;


     
pPAB           = &Pab;


   }


else


      pPAB
= NULL;


 


if (error =
EditorAppendBitmapToNote(EPBContext.hBitmap,


               (WORD)(WIDTH
\* ONEINCH), 


           
(WORD)(HEIGHT \* ONEINCH), 


           
100,


               hTargetNote,



           
0, 


           
"Body", 


           
strlen("Body"), 


           
pPAB))


   
printf("Can't append bitmap: %e\n", error);


 


 **See Also :**


**[CDPABDEFINITION](CDPABDEFINITION.md)**


**[EditorPrintNoteToBitmap](EditorPrintNoteToBitmap.md)**


**[EPBCONTEXT](EPBCONTEXT.md)**


**[ITEM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/00F200B70087008C85255E2D007931E6)**



----------------------------------------------------------------------------------------------------------


 





