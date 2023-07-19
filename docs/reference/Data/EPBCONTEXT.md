##### Data Type : Edit Fax
##### EPBCONTEXT - Data structure used by the EditorPrintNoteToBitmap Editfax API.
---
```
#include <editfax.h>
```

**Definition :**

typedef struct {
   EPBPROC  Proc;         /* Callback procedure */
   HPAINT   hPaint;       /* hPS that the bitmap can be selected
                             into */
   HBITMAP  hBitmap;      /* Bitmap to paint into */
   RECTSIZE BitmapSize;   /* Size of the bitmap */
   RECT     PaintRect;    /* Rectangle within the bitmap into which
                             to paint */
   WORD     cxPaperTwips; /* Width of the paper, in TWIPS */
   WORD     cyPaperTwips; /* Height of the paper, in TWIPS */
} EPBCONTEXT;

**Description :**

This data structure contains the name of the callback routine, and other information which are passed to the callback routine by the EditorPrintNoteToBitmap Editfax API.


**Sample Usage :**
```
	
EPBCONTEXT EPBContext;
.
.
.

error = EditorPrintNoteToBitmap(hSourceDB,
                                SourceNoteID,
                                &EPBContext);

```

**See Also :**
[EditorPrintNoteToBitmap](/domino-c-api-docs/reference/Func/EditorPrintNoteToBitmap)
[HPAINT](/domino-c-api-docs/reference/Data/HPAINT)
[RECTSIZE](/domino-c-api-docs/reference/Data/RECTSIZE)
---
