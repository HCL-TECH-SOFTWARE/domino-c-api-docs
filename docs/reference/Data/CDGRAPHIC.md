##### Data Type : Rich Text
##### CDGRAPHIC - Graphic combination object record
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   LSIG     Header;     /* Signature and Length */
   RECTSIZE DestSize;   /* Destination Display size in TWIPS
                           (1/1440 inch) */
   RECTSIZE CropSize;   /* Reserved */
   CROPRECT CropOffset; /* Reserved */
   WORD     fResize;    /* True if user resized object */
   BYTE     Version;    /* CDGRAPHIC_VERSIONxxx */
   BYTE     bFlags;     /* Ignored before CDGRAPHIC_VERSION3 */
      WORD     wReserved;
} CDGRAPHIC;
```

**Description :**

The CDGRAPHIC record contains information used to control display of graphic objects in a document.  This record marks the beginning of a composite graphic object, and must be present for any graphic object to be loaded or displayed.<br>
<br>
A composite graphic object may be one or more of the following:<br>
<br>
<tt><font size="2">&nbsp; &nbsp;CDCGMMETA<br>
 &nbsp; CDWINMETAHEADER<br>
 &nbsp; CDWINMETASEG<br>
 &nbsp; CDPMMETAHEADER<br>
 &nbsp; CDPMMETASEG<br>
 &nbsp; CDMACMETAHEADER<br>
 &nbsp; CDMACMETASEG<br>
 &nbsp; CDBITMAPHEADER<br>
 &nbsp; CDBITMAPSEGMENT</font></tt>
<ul><br>
<tt><font size="2">&nbsp; &nbsp;CDCOLORTABLE</font></tt><br>
<br>
If more than one graphic object is present, Notes will only display one, using the following precedence rules:<br>
<br>
	1)  If there is a CGM metafile object, display it<br>
	2)  If there is a native metafile object for this platform, display it<br>
	3)  If there is a bitmap, display it<br>
<br>
The fields in this record are:<br>
<br>
<tt><font size="2">&nbsp; &nbsp;Header &nbsp; &nbsp; Tag identifying this as a CDGRAPHIC record<br>
 &nbsp; DestSize &nbsp; Destination display area, measured in &quot;twips&quot;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; (1/1440 of an inch) or in pixels.<br>
 &nbsp; CropSize &nbsp; Reserved; &nbsp;set all fields in this structure to 0<br>
 &nbsp; CropOffset Reserved; set all fields in this structure to 0<br>
 &nbsp; fResize &nbsp; &nbsp;If the user resizes the graphic object, this field is</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; set to TRUE<br>
 &nbsp; Version &nbsp; &nbsp;Version number of the Domino graphics driver</font></tt><br>
<tt><font size="2">	bFlags	See </font></tt><tt><font size="2">CDGRAPHIC_FLAG_xxx.</font></tt></ul>



**See Also :**
[CDBITMAPHEADER](/domino-c-api-docs/reference/Data/CDBITMAPHEADER)
[CDBITMAPSEGMENT](/domino-c-api-docs/reference/Data/CDBITMAPSEGMENT)
[CDCGMMETA](/domino-c-api-docs/reference/Data/CDCGMMETA)
[CDGRAPHIC_FLAG_xxx](/domino-c-api-docs/reference/Symb/CDGRAPHIC_FLAG_xxx)
[CDGRAPHIC_VERSIONxxx](/domino-c-api-docs/reference/Symb/CDGRAPHIC_VERSIONxxx)
[CDMACMETAHEADER](/domino-c-api-docs/reference/Data/CDMACMETAHEADER)
[CDMACMETASEG](/domino-c-api-docs/reference/Data/CDMACMETASEG)
[CDPMMETAHEADER](/domino-c-api-docs/reference/Data/CDPMMETAHEADER)
[CDPMMETASEG](/domino-c-api-docs/reference/Data/CDPMMETASEG)
[CDWINMETAHEADER](/domino-c-api-docs/reference/Data/CDWINMETAHEADER)
[CDWINMETASEG](/domino-c-api-docs/reference/Data/CDWINMETASEG)
[CROPRECT](/domino-c-api-docs/reference/Data/CROPRECT)
[RECTSIZE](/domino-c-api-docs/reference/Data/RECTSIZE)
---
