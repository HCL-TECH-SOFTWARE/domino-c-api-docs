##### Data Type : Composite Data
##### CDPMMETAHEADER - Start of a Presentation Manager GPI Metafile Record
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
   LSIG     Header;           /* Signature and Length */
   SWORD    mm;               /* PM mapping mode */
   SWORD    xExt,yExt;        /* Extents, in world coordinates */
   RECTSIZE OriginalDisplaySize; /* Original disp. size, in twips */
   DWORD    MetafileSize;     /* Total size of metafile, in bytes */
   WORD     SegCount;         /* Number of CDPMMETASEG records */
/* Metafile segments follow... */
} CDPMMETAHEADER;

**Description :**

Identifies a Presentation Manger GPI metafile embedded in a rich text field.  This record must be preceded by a CDGRAPHIC record.  Since metafiles can be large, but Domino and Notes have an internal limit of 65,536 bytes (64kB) for a segment, a metafile may be divided into segments of up to 64kB;  each segment must be preceded by a CDPMMETASEG record.<br>
<br>
<tt><font size="2">&nbsp; Header &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Tag identifying this as a CDPMMETAHEADER record<br>
 &nbsp;mm &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; PM mapping mode<br>
 &nbsp;xExt &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Width of drawing in world coordinates<br>
 &nbsp;yExt &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Height of drawing in world coordinates<br>
 &nbsp;OriginalDisplaySize &nbsp;Original display size of metafile,</font></tt>
<ul><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;measured in &quot;twips&quot; (1/1440 inch)<br>
 &nbsp;MetafileSize &nbsp; &nbsp; &nbsp; Total size of metafile data in bytes<br>
 &nbsp;SegCount &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Number of CDPMMETASEG records<br>
</font></tt><br>
This header is followed by the segments of metafile data.</ul>



**See Also :**
[CDGRAPHIC](/domino-c-api-docs/reference/Data/CDGRAPHIC)
[CDPMMETASEG](/domino-c-api-docs/reference/Data/CDPMMETASEG)
---
