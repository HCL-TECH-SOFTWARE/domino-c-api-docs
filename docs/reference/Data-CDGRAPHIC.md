##### Data Type : Rich Text
##### CDGRAPHIC - Graphic combination object record
---
##### #include <editods.h>
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
[CDBITMAPHEADER](D:/md_files/CDBITMAPHEADER.md)
[CDBITMAPSEGMENT](D:/md_files/CDBITMAPSEGMENT.md)
[CDCGMMETA](D:/md_files/CDCGMMETA.md)
[CDGRAPHIC_FLAG_xxx](D:/md_files/CDGRAPHIC_FLAG_xxx.md)
[CDGRAPHIC_VERSIONxxx](D:/md_files/CDGRAPHIC_VERSIONxxx.md)
[CDMACMETAHEADER](D:/md_files/CDMACMETAHEADER.md)
[CDMACMETASEG](D:/md_files/CDMACMETASEG.md)
[CDPMMETAHEADER](D:/md_files/CDPMMETAHEADER.md)
[CDPMMETASEG](D:/md_files/CDPMMETASEG.md)
[CDWINMETAHEADER](D:/md_files/CDWINMETAHEADER.md)
[CDWINMETASEG](D:/md_files/CDWINMETASEG.md)
[CROPRECT](D:/md_files/CROPRECT.md)
[RECTSIZE](D:/md_files/RECTSIZE.md)
---
