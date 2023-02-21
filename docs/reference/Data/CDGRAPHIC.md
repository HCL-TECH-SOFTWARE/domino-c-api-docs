##### Data Type : Rich Text
##### CDGRAPHIC - Graphic combination object record
---
```
#include <editods.h>
```
**Description :**

The CDGRAPHIC record contains information used to control display of graphic 
objects in a document.  This record marks the beginning of a composite graphic 
object, and must be present for any graphic object to be loaded or displayed.

A composite graphic object may be one or more of the following:

   CDCGMMETA
   CDWINMETAHEADER
   CDWINMETASEG
   CDPMMETAHEADER
   CDPMMETASEG
   CDMACMETAHEADER
   CDMACMETASEG
   CDBITMAPHEADER
   CDBITMAPSEGMENT
   CDCOLORTABLE

If more than one graphic object is present, Notes will only display one, using 
the following precedence rules:

 1)  If there is a CGM metafile object, display it
 2)  If there is a native metafile object for this platform, display it
 3)  If there is a bitmap, display it

The fields in this record are:

   Header     Tag identifying this as a CDGRAPHIC record
   DestSize   Destination display area, measured in "twips"
              (1/1440 of an inch) or in pixels.
   CropSize   Reserved;  set all fields in this structure to 0
   CropOffset Reserved; set all fields in this structure to 0
   fResize    If the user resizes the graphic object, this field is
              set to TRUE
   Version    Version number of the Domino graphics driver
	bFlags See CDGRAPHIC_FLAG_xxx.

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
