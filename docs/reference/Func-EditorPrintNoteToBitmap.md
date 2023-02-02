##### Function : Edit Fax
##### EditorPrintNoteToBitmap - An Editfax API - rendering a note to a FAX bitmap
---
##### #include <editfax.h>
STATUS far PASCAL **EditorPrintNoteToBitmap(**

	DBHANDLE  hDB,
	NOTEID  NoteID,
	void *EPBContext);
**Description :**
This API is supported for the Intel Windows 32-bit environment only.

For each page in the specified note, this API calls the callback routine 
specified in the EPBContext structure and prints the page content to a FAX 
bitmap.  The definition of the callback routine is: 

typedef BOOL (FAR PASCAL * EPBPROC)(
   void *EPBContext,
   WORD PageNumber);

Note that the database hosting the note must have a default view; otherwise, 
this API will give a "floating point not loaded" error.

**Parameters :**
Input :
hDB  -  Handle of the database containing document to be FAXed.

NoteID  -  NoteID of the document to be FAXed.

EPBContext  -  Structure to be used in the callback routine.  This parameter must either be a pointer to an EPBCONTEXT or a pointer to a structure whose first field is an EPBCONTEXT (this second way allows the programmer to add their own additional context information).

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


**Sample Usage :**
```
   EPBCONTEXT EPBContext;
   HBITMAP    hPrevBitmap;
   HBRUSH     hBrush, hPrevBrush;
   RECT       Rect;

   .
   .
   .

   memset(&EPBContext, 0, sizeof(EPBContext));

   /*   Set up the resolution parameters */ 

   EPBContext.cxPaperTwips = (DWORD) (WIDTH * ONEINCH);
   EPBContext.cyPaperTwips = (DWORD) (HEIGHT * ONEINCH);
   EPBContext.BitmapSize.width = (DWORD) (WIDTH * DPI);
   EPBContext.BitmapSize.height = (DWORD) (HEIGHT * DPI);

   /*   Set up pointer to callback routine */

   EPBContext.Proc = (EPBPROC) ProcessBitmap;

   /*   Creates a memory device context compatible with the
        application's current screen.  */  

   EPBContext.hPaint = CreateCompatibleDC(NULL);

   if (!EPBContext.hPaint)
      {
      printf("Cannot create memory DC\n");
      return(NOERROR);  
      }

   /*  Create a bitmap  */

   EPBContext.hBitmap= CreateBitmap(EPBContext.BitmapSize.width,
                                    EPBContext.BitmapSize.height, 
                                    (BYTE) 1,(BYTE) 1, NULL);

   /*  Preset the bitmap to BLACK with a 10-pixel border and set the
       subset paint rectangle so that we can test to see that printing
       to a subset rect is working. */

   hPrevBitmap = (HBITMAP) SelectObject(EPBContext.hPaint, 
                                        (HANDLE)EPBContext.hBitmap);

   Rect.left   = Rect.top = 0;
   Rect.right  = EPBContext.BitmapSize.width;
   Rect.bottom = EPBContext.BitmapSize.height;
   
   hBrush = CreateSolidBrush(0x02000000L | (RGBVALUE_BLACK)); /* Create a Brush 
                                                                 graphic object 
*/
   hPrevBrush = SelectObject(EPBContext.hPaint, hBrush); 

   PatBlt(EPBContext.hPaint, (&Rect)->left,   /* Paints the given rectangle  */
               (&Rect)->top,                  /* using the brush that is     
*/        (&Rect)->right-(&Rect)->left,  /* currently selected into the 
*/          
	    (&Rect)->bottom-(&Rect)->top,  /* specified device context.   */
               PATCOPY); 

   SelectObject(EPBContext.hPaint, hPrevBrush); 
   
   SelectObject(EPBContext.hPaint, (HANDLE)hPrevBitmap);

   EPBContext.PaintRect.top    = EPBContext.PaintRect.left   = 10;
   EPBContext.PaintRect.right  = EPBContext.BitmapSize.width - 10;
   EPBContext.PaintRect.bottom = EPBContext.BitmapSize.height- 10;

   /*   Print the note to the bitmaps */

   error = EditorPrintNoteToBitmap(hSourceDB,
               SourceNoteID,
               &EPBContext);

   /*   Clean up. */

   DeleteObject(hBrush);
   DeleteObject(EPBContext.hBitmap);
   DeleteDC(EPBContext.hPaint);

```
**See Also :**
[EditorAppendBitmapToNote](D:/md_files/EditorAppendBitmapToNote.md)
[EPBCONTEXT](D:/md_files/EPBCONTEXT.md)
[EPBPROC](D:/md_files/EPBPROC.md)
---
