##### Function : Edit Fax
##### EditorAppendBitmapToNote - An Editfax API - appending a FAX bitmap to a note.
---
##### #include <editfax.h>
STATUS far PASCAL **EditorAppendBitmapToNote(**

	HBITMAP  hBitmap,
	WORD  cxPaperTwips,
	WORD  cyPaperTwips,
	WORD  DisplayScalingPercent,
	NOTEHANDLE  hNote,
	WORD  ItemFlags,
	char *ItemName,
	WORD  ItemNameLength,
	void *ParagraphAttributes);
**Description :**
This API is supported in the Intel Windows 32-bit environment only.

This Editfax API appends a FAX bitmap to a specified item in a specified note.  
**Parameters :**
Input :
hBitmap  -  Handle to a FAX bitmap.

cxPaperTwips  -  Width of the paper, in TWIPS.

cyPaperTwips  -  Height of the paper, in TWIPS.

DisplayScalingPercent  -  The scaling factor to be used when appending the bitmap to the note.  100 indicates retaining the original bitmap size.

hNote  -  Handle of the note the FAX bitmap will be appended to.

ItemFlags  -  These flags are defined in ITEM_xxx.

ItemName  -  Name of the rich text item the FAX bitmap will be appended to.

ItemNameLength  -  Length of the "ItemName".

ParagraphAttributes  -  The format of the rich-text paragraph.  See CDPABDEFINITION for the format structure.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


**Sample Usage :**
```
  .
  .
  .

if (PageNumber > 1)     /* add a paragraph */
   {
      memset(&Pab, 0, sizeof(CDPABDEFINITION));
      Pab.Flags      = PABFLAG_PAGINATE_BEFORE | PABFLAG_PROPAGATE;
      Pab.LeftMargin = Pab.FirstLineLeftMargin = ONEINCH;
      Pab.PABID      = 0xffff;
      pPAB           = &Pab;
   }
else
      pPAB = NULL;
 
if (error = EditorAppendBitmapToNote(EPBContext.hBitmap,
	 (WORD)(WIDTH * ONEINCH), 
            (WORD)(HEIGHT * ONEINCH), 
            100,
	 hTargetNote, 
            0, 
            "Body", 
            strlen("Body"), 
            pPAB))
    printf("Can't append bitmap: %e\n", error);

```
**See Also :**
[CDPABDEFINITION](D:/md_files/CDPABDEFINITION.md)
[EditorPrintNoteToBitmap](D:/md_files/EditorPrintNoteToBitmap.md)
[EPBCONTEXT](D:/md_files/EPBCONTEXT.md)
[ITEM_xxx](D:/md_files/ITEM_xxx.md)
---
