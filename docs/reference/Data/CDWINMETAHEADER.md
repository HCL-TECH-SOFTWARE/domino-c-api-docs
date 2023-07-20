##### Data Type : Composite Data
##### CDWINMETAHEADER - Start of a Windows GDI Metafile Record
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   LSIG     Header;           /* Signature and Length */
   SWORD    mm;               /* Windows mapping mode */
   SWORD    xExt,yExt;        /* Extents, in world coordinates */
   RECTSIZE OriginalDisplaySize; /* Original disp. size, in twips */
   DWORD    MetafileSize;     /* Total size of metafile, in bytes */
   WORD     SegCount;         /* Number of CDWINMETASEG records */
/* Metafile segments follow... */
} CDWINMETAHEADER;
```

**Description :**

Identifies a Windows Graphics Device Interface (GDI) metafile embedded in a rich text field.  This record must be preceded by a CDGRAPHIC record.  Since Windows GDI metafiles can be large, but Domino and Notes have an internal limit of 65,536 bytes (64kB) for a segment, a metafile may be divided into segments of up to 64kB;  each segment must be preceded by a CDWINMETASEG record.<br>
<br>
<tt><font size="2">&nbsp; Header &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Tag identifying this as a CDWINMETAHEADER record<br>
 &nbsp;mm &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Windows mapping mode<br>
 &nbsp;xExt &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Width of drawing in world coordinates<br>
 &nbsp;yExt &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Height of drawing in world coordinates<br>
 &nbsp;OriginalDisplaySize Original Display size of metafile,</font></tt>
<ul><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; measured in &quot;twips&quot; (1/1440 inch)<br>
 &nbsp;MetafileSize &nbsp; &nbsp; &nbsp;Total size of metafile data in bytes<br>
 &nbsp;SegCount &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Number of CDWINMETASEG records<br>
</font></tt><br>
This header is followed by the segments of metafile data.</ul>



**See Also :**
[CDGRAPHIC](/domino-c-api-docs/reference/Data/CDGRAPHIC)
[CDWINMETASEG](/domino-c-api-docs/reference/Data/CDWINMETASEG)
---
