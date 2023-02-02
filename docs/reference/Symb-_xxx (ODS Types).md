##### Symbolic Value : Canonical Format Conversion
##### _xxx (ODS Types) - Identifies the Domino data structure to ODS functions.
---
##### #include <odstypes.h>
**Description :**
You must specify one of these symbols as the type input to ODSLength, 
ODSReadMemory, and ODSWriteMemory.

You must call ODSReadMemory to convert data structures from Domino canonical 
format to machine-specific (host) format, and ODSWriteMemory to convert a data 
structure from host format to Domino canonical format.

Your API program must perform this conversion if (1) it runs on non-Intel 
architecture machines, and (2) it is reading or writing item data of one of the 
following data types:

    TYPE_COMPOSITE
    TYPE_COLLATION
    TYPE_OBJECT
    TYPE_VIEW_FORMAT
    TYPE_ICON
    TYPE_SIGNATURE
    TYPE_SEAL
    TYPE_SEALDATA
    TYPE_SEAL_LIST
    TYPE_WORKSHEET_DATA
    TYPE_USERDATA
    TYPE_QUERY
    TYPE_ACTION
    TYPE_ASSISTANT_INFO
    TYPE_VIEWMAP_DATASET
    TYPE_VIEWMAP_LAYOUT
    TYPE_CALENDAR_FORMAT

Your API program must not perform conversion when accessing items of any other 
data type, or when accessing non-item data (Domino and Notes automatically 
performs the conversion for you in these cases).

From ods.h:
/* Base ODS types */

#define _SHORT 0
#define _USHORT _SHORT
#define _WORD _SHORT
#define _STATUS _SHORT
#define _UNICODE _SHORT
#define _LONG 1
#define _FLOAT 2
#define _DWORD _LONG
#define _ULONG _LONG

/* ODS types that are the size of a base type */

#define _NUMBER _FLOAT
#define _NOTEID _LONG

/* Include the rest of the ODS types from odstypes.h */

#if defined(GCC) && defined(SUN)
#define odsmacro(name, num, size) enum{_/*##*/name = num};
#else
#define odsmacro(name, num, size) enum{_##name = num};
#endif
#include "odstypes.h"
#undef odsmacro


From odstypes.h:
odsmacro(TIMEDATE,10,sizeof(TIMEDATE))
odsmacro(TIMEDATE_PAIR,11,sizeof(TIMEDATE_PAIR))
odsmacro(ALIGNED_NUMBER_PAIR,12,sizeof(ALIGNED_NUMBER_PAIR))
odsmacro(LIST,13,sizeof(LIST))
odsmacro(RANGE,14,sizeof(RANGE))
odsmacro(DBID,15,sizeof(DBID))
odsmacro(ITEM,17,sizeof(ITEM))
odsmacro(ITEM_TABLE,18,sizeof(ITEM_TABLE))
odsmacro(SEARCH_MATCH,24,sizeof(SEARCH_MATCH))
odsmacro(ORIGINATORID,26,sizeof(ORIGINATORID))
#define _OID _ORIGINATORID
odsmacro(OBJECT_DESCRIPTOR,27,sizeof(OBJECT_DESCRIPTOR))
odsmacro(UNIVERSALNOTEID,28,sizeof(UNIVERSALNOTEID))
#define _UNID _UNIVERSALNOTEID
odsmacro(VIEW_TABLE_FORMAT,29,sizeof(VIEW_TABLE_FORMAT))
odsmacro(VIEW_COLUMN_FORMAT,30,sizeof(VIEW_COLUMN_FORMAT))
odsmacro(NOTELINK,33,sizeof(NOTELINK))
odsmacro(LICENSEID,34,sizeof(LICENSEID))
odsmacro(VIEW_FORMAT_HEADER,42,sizeof(VIEW_FORMAT_HEADER))
odsmacro(VIEW_TABLE_FORMAT2,43,sizeof(VIEW_TABLE_FORMAT2))
odsmacro(DBREPLICAINFO,56,sizeof(DBREPLICAINFO))
odsmacro(FILEOBJECT,58,sizeof(FILEOBJECT))
odsmacro(COLLATION,59,sizeof(COLLATION))
odsmacro(COLLATE_DESCRIPTOR,60,sizeof(COLLATE_DESCRIPTOR))
odsmacro(CDKEYWORD,68,sizeof(CDKEYWORD))
odsmacro(CDLINK2,72,sizeof(CDLINK2))
odsmacro(CDLINKEXPORT2,97,sizeof(CDLINKEXPORT2))
odsmacro(CDPARAGRAPH,109,sizeof(CDPARAGRAPH))
odsmacro(CDPABDEFINITION,110,sizeof(CDPABDEFINITION))
odsmacro(CDPABREFERENCE,111,sizeof(CDPABREFERENCE))
odsmacro(CDFIELD_PRE_36,112,sizeof(CDFIELD_PRE_36))
odsmacro(CDTEXT,113,sizeof(CDTEXT))
odsmacro(CDDOCUMENT,114,sizeof(CDDOCUMENT))
odsmacro(CDMETAFILE,115,sizeof(CDMETAFILE))
odsmacro(CDBITMAP,116,sizeof(CDBITMAP))
odsmacro(CDHEADER,117,sizeof(CDHEADER))
odsmacro(CDFIELD,118,sizeof(CDFIELD))
odsmacro(CDFONTTABLE,119,sizeof(CDFONTTABLE))
odsmacro(CDFACE,120,sizeof(CDFACE))
odsmacro(CDCGM,156,sizeof(CDCGM))
odsmacro(CDTIFF,159,sizeof(CDTIFF))
odsmacro(CDBITMAPHEADER,162,sizeof(CDBITMAPHEADER))
odsmacro(CDBITMAPSEGMENT,163,sizeof(CDBITMAPSEGMENT))
odsmacro(CDCOLORTABLE,164,sizeof(CDCOLORTABLE))
odsmacro(CDPATTERNTABLE,165,sizeof(CDPATTERNTABLE))
odsmacro(CDGRAPHIC,166,sizeof(CDGRAPHIC))
odsmacro(CDPMMETAHEADER,167,sizeof(CDPMMETAHEADER))
odsmacro(CDWINMETAHEADER,168,sizeof(CDWINMETAHEADER))
odsmacro(CDMACMETAHEADER,169,sizeof(CDMACMETAHEADER))
odsmacro(CDCGMMETA,170,sizeof(CDCGMMETA))
odsmacro(CDPMMETASEG,171,sizeof(CDPMMETASEG))
odsmacro(CDWINMETASEG,172,sizeof(CDWINMETASEG))
odsmacro(CDMACMETASEG,173,sizeof(CDMACMETASEG))
odsmacro(CDDDEBEGIN,174,BIGGERTHANABYTE)
odsmacro(CDDDEEND,175,sizeof(CDDDEEND))
odsmacro(CDTABLEBEGIN,176,sizeof(CDTABLEBEGIN))
odsmacro(CDTABLECELL,177,sizeof(CDTABLECELL))
odsmacro(CDTABLEEND,178,sizeof(CDTABLEEND))
odsmacro(CDSTYLENAME,188,sizeof(CDSTYLENAME))
odsmacro(FILEOBJECT_MACEXT,192,sizeof(FILEOBJECT_MACEXT))
odsmacro(FILEOBJECT_HPFSEXT,193,sizeof(FILEOBJECT_HPFSEXT))
odsmacro(CDOLEBEGIN,218,sizeof(CDOLEBEGIN))
odsmacro(CDOLEEND,219,sizeof(CDOLEEND))
odsmacro(CDHOTSPOTBEGIN,230,sizeof(CDHOTSPOTBEGIN))
odsmacro(CDHOTSPOTEND,231,sizeof(CDHOTSPOTEND))
odsmacro(CDBUTTON, 237, sizeof (CDBUTTON))
odsmacro(CDBAR, 308, sizeof(CDBAR))
odsmacro(CDQUERYHEADER,314,sizeof(CDQUERYHEADER))
odsmacro(CDQUERYTEXTTERM,315,sizeof(CDQUERYTEXTTERM))
odsmacro(CDACTIONHEADER,316,sizeof(CDACTIONHEADER))
odsmacro(CDACTIONMODIFYFIELD,317,sizeof(CDACTIONMODIFYFIELD))
odsmacro(ODS_ASSISTSTRUCT,318,sizeof(ODS_ASSISTSTRUCT))
odsmacro(VIEWMAP_HEADER_RECORD,319,sizeof(VIEWMAP_HEADER_RECORD))
odsmacro(VIEWMAP_RECT_RECORD,320,sizeof(VIEWMAP_RECT_RECORD))
odsmacro(VIEWMAP_BITMAP_RECORD,321,sizeof(VIEWMAP_BITMAP_RECORD))
odsmacro(VIEWMAP_REGION_RECORD,322,sizeof(VIEWMAP_REGION_RECORD))
odsmacro(VIEWMAP_POLYGON_RECORD,323,sizeof(VIEWMAP_POLYGON_RECORD))
odsmacro(VIEWMAP_POLYLINE_RECORD,324,sizeof(VIEWMAP_POLYLINE_RECORD)
odsmacro(VIEWMAP_ACTION_RECORD,325,sizeof(VIEWMAP_ACTION_RECORD))
odsmacro(ODS_ASSISTRUNINFO,326,sizeof(ODS_ASSISTRUNINFO))
odsmacro(CDACTIONREPLY,327,sizeof(CDACTIONREPLY))
odsmacro(CDACTIONFORMULA,332,sizeof(CDACTIONFORMULA))
odsmacro(CDACTIONLOTUSSCRIPT,333,sizeof(CDACTIONLOTUSSCRIPT))
odsmacro(CDQUERYBYFIELD,334,sizeof(CDQUERYBYFIELD))
odsmacro(CDACTIONSENDMAIL,335,sizeof(CDACTIONSENDMAIL))
odsmacro(CDACTIONDBCOPY,336,sizeof(CDACTIONDBCOPY))
odsmacro(CDACTIONDELETE,337,sizeof(CDACTIONDELETE))
odsmacro(CDACTIONBYFORM,338,sizeof(CDACTIONBYFORM))
odsmacro(ODS_ASSISTFIELDSTRUCT,339,sizeof(ODS_ASSISTFIELDSTRUCT))
odsmacro(CDACTION, 340, sizeof(CDACTION))
odsmacro(CDACTIONREADMARKS,341,sizeof(CDACTIONREADMARKS))
odsmacro(CDEXTFIELD,342,sizeof(CDEXTFIELD))
odsmacro(CDLAYOUT,343,sizeof(CDLAYOUT))
odsmacro(CDLAYOUTTEXT,344,sizeof(CDLAYOUTTEXT))
odsmacro(CDLAYOUTEND,345,sizeof(CDLAYOUTEND))
odsmacro(CDLAYOUTFIELD,346,sizeof(CDLAYOUTFIELD))
odsmacro(VIEWMAP_DATASET_RECORD,347,BIGGERTHANABYTE)
odsmacro(CDDOCAUTOLAUNCH,350,sizeof(CDDOCAUTOLAUNCH))
odsmacro(CDPABHIDE, 358, sizeof(CDPABHIDE))
odsmacro(CDPABFORMULAREF, 359, sizeof(CDPABFORMULAREF))
odsmacro(CDACTIONBAR, 360, sizeof(CDACTIONBAR))
odsmacro(CDACTIONFOLDER,361,sizeof(CDACTIONFOLDER))
odsmacro(CDACTIONNEWSLETTER,362,sizeof(CDACTIONNEWSLETTER))
odsmacro(CDACTIONRUNAGENT,363,sizeof(CDACTIONRUNAGENT))
odsmacro(CDACTIONSENDDOCUMENT,364,sizeof(CDACTIONSENDDOCUMENT))
odsmacro(CDQUERYFORMULA,365,sizeof(CDQUERYFORMULA))
odsmacro(CDQUERYBYFORM,373,sizeof(CDQUERYBYFORM))
odsmacro(ODS_ASSISTRUNOBJECTHEADER,374,sizeof(ODS_ASSISTRUNOBJECTHEADER))
odsmacro(ODS_ASSISTRUNOBJECTENTRY,375,sizeof(ODS_ASSISTRUNOBJECTENTRY))
odsmacro(CDLAYOUTGRAPHIC,407,sizeof(CDLAYOUTGRAPHIC))
odsmacro(CDQUERYBYFOLDER,413,sizeof(CDQUERYBYFOLDER))
odsmacro(CDQUERYUSESFORM,423,sizeof(CDQUERYUSESFORM))
odsmacro(VIEW_COLUMN_FORMAT2, 428, sizeof(VIEW_COLUMN_FORMAT2))
odsmacro(VIEWMAP_TEXT_RECORD,464,sizeof(VIEWMAP_TEXT_RECORD))
odsmacro(CDLAYOUTBUTTON,466,sizeof(CDLAYOUTBUTTON))
odsmacro(CDQUERYTOPIC,471,sizeof(CDQUERYTOPIC))
odsmacro(CDLSOBJECT,482,sizeof(CDLSOBJECT))
odsmacro(CDHTMLHEADER,492,sizeof(CDHTMLHEADER))
odsmacro(CDHTMLSEGMENT,493,sizeof(CDHTMLSEGMENT))odsmacro(SCHED_LIST,502,sizeof(
SCHED_LIST))
#define _SCHED_LIST_OBJ _SCHED_LIST
odsmacro(SCHED_ENTRY,503,sizeof(SCHED_ENTRY))
odsmacro(SCHEDULE,504,sizeof(SCHEDULE))
odsmacro(CDTEXTEFFECT,508,sizeof(CDTEXTEFFECT))
odsmacro(VIEW_CALENDAR_FORMAT,513,sizeof(VIEW_CALENDAR_FORMAT))
odsmacro(CDSTORAGELINK,515,sizeof(CDSTORAGELINK))
odsmacro(ACTIVEOBJECT,516,sizeof(ACTIVEOBJECT))
odsmacro(ACTIVEOBJECTPARAM,517,sizeof(ACTIVEOBJECTPARAM))
odsmacro(ACTIVEOBJECTSTORAGELINK,518,sizeof(ACTIVEOBJECTSTORAGELINK))odsmacro(CD
TRANSPARENTTABLE,541,sizeof(CDTRANSPARENTTABLE))
/* modified viewmap records, changed CD record from byte to word */
odsmacro(VIEWMAP_POLYGON_RECORD,551,sizeof(VIEWMAP_POLYGON_RECORD))
odsmacro(VIEWMAP_POLYLINE_RECORD,552,sizeof(VIEWMAP_POLYLINE_RECORD))
odsmacro(SCHED_DETAIL_LIST,553,sizeof(SCHED_DETAIL_LIST))
odsmacro(CDALTERNATEBEGIN,554,sizeof(CDALTERNATEBEGIN))
odsmacro(CDALTERNATEEND,555,sizeof(CDALTERNATEEND))
odsmacro(CDOLERTMARKER,556,sizeof(CDOLERTMARKER))
odsmacro(HSOLERICHTEXT,557,sizeof(HSOLERICHTEXT))
odsmacro(CDANCHOR, 559, sizeof(CDANCHOR))
odsmacro(CDHRULE, 560, sizeof (CDHRULE))
odsmacro(CDALTTEXT, 561, sizeof(CDALTTEXT))
odsmacro(CDACTIONJAVAAGENT,562,sizeof(CDACTIONJAVAAGENT))
odsmacro(CDHTMLBEGIN, 564, sizeof(CDHTMLBEGIN))
odsmacro(CDHTMLEND, 565, sizeof(CDHTMLEND))
odsmacro(CDHTMLFORMULA, 566, sizeof(CDHTMLFORMULA))
odsmacro(CDBEGINRECORD, 577, sizeof (CDBEGINRECORD))
odsmacro(CDENDRECORD, 578, sizeof (CDENDRECORD))
odsmacro(CDVERTICALALIGN, 579, sizeof (CDVERTICALALIGN))
odsmacro(CDFLOAT, 580, sizeof (CDFLOAT))
odsmacro(CDTIMERINFO, 581, sizeof (CDTIMERINFO))
odsmacro(CDTABLEROWHEIGHT, 582, sizeof (CDTABLEROWHEIGHT))
odsmacro(CDTABLELABEL, 583, sizeof (CDTABLELABEL))
odsmacro(CDTRANSITION, 610, sizeof (CDTRANSITION))
odsmacro(CDPLACEHOLDER, 611, sizeof (CDPLACEHOLDER))
odsmacro(CDEMBEDDEDVIEW, 615, sizeof (CDEMBEDDEDVIEW))
odsmacro(CDEMBEDDEDOUTLINE, 620, BIGGERTHANABYTE)
odsmacro(CDREGIONBEGIN, 621, sizeof(CDREGIONBEGIN))
odsmacro(CDREGIONEND, 622, sizeof(CDREGIONEND))
odsmacro(CDCELLBACKGROUNDDATA, 623, sizeof (CDCELLBACKGROUNDDATA))
odsmacro(FRAMESETLENGTH, 625, sizeof(FRAMESETLENGTH))
odsmacro(CDFRAMESETHEADER, 626, sizeof(CDFRAMESETHEADER))
odsmacro(CDFRAMESET, 627, sizeof(CDFRAMESET))
odsmacro(CDFRAME, 628, sizeof(CDFRAME))
odsmacro(CDTARGET, 629, sizeof(CDTARGET))
odsmacro(CDRESOURCE, 631, sizeof(CDRESOURCE))
odsmacro(CDMAPELEMENT, 632, sizeof(CDMAPELEMENT))
odsmacro(CDAREAELEMENT, 633, sizeof(CDAREAELEMENT))
odsmacro(CDRECT, 634, sizeof(CDRECT))
odsmacro(CDPOINT, 635, sizeof(CDPOINT))
odsmacro(CDEMBEDDEDCTL, 636, sizeof (CDEMBEDDEDCTL))
odsmacro(CDEVENT, 637, sizeof(CDEVENT))
odsmacro(MIME_PART, 639, sizeof(MIME_PART))
odsmacro(CDPRETABLEBEGIN,640,sizeof(CDPRETABLEBEGIN))
odsmacro(CDCOLOR,645,sizeof(CDCOLOR))
odsmacro(CDBORDERINFO, 646, sizeof (CDBORDERINFO))
odsmacro(CDEXT2FIELD,672,sizeof(CDEXT2FIELD))
odsmacro(CDEMBEDDEDSCHEDCTL, 674, sizeof(CDEMBEDDEDSCHEDCTL))
odsmacro(RFC822ITEMDESC,675,sizeof(RFC822ITEMDESC))
odsmacro(COLOR_VALUE,690,sizeof(COLOR_VALUE))
odsmacro(CDBLOBPART,695,sizeof(CDBLOBPART))
odsmacro(CDIMAGEHEADER, 705, sizeof(CDIMAGEHEADER))
odsmacro(CDIMAGESEGMENT, 706, sizeof(CDIMAGESEGMENT))
odsmacro(VIEW_TABLE_FORMAT3, 707, sizeof(VIEW_TABLE_FORMAT3))
odsmacro(CDIDNAME, 708, sizeof(CDIDNAME))
odsmacro(CDACTIONBAREXT,719,sizeof(CDACTIONBAREXT))
odsmacro(CDLINKCOLORS,722,sizeof(CDLINKCOLORS))
odsmacro(CDCAPTION,728,sizeof(CDCAPTION))
odsmacro(CDFIELDHINT,742,sizeof(CDFIELDHINT))
odsmacro(CDLSOBJECT_R6,744,sizeof(CDLSOBJECT_R6))
odsmacro(CDINLINE, 756, sizeof(CDINLINE))
odsmacro(CDTEXTPROPERTIESTABLE,765,sizeof(CDTEXTPROPERTIESTABLE))
odsmacro(CDSPANRECORD,766,sizeof(CDSPANRECORD))
odsmacro(CDDECSFIELD, 767, sizeof(CDDECSFIELD))
odsmacro(CDLAYER, 808, sizeof(CDLAYER))
odsmacro(CDPOSITIONING, 809, sizeof(CDPOSITIONING))
odsmacro(CDBOXSIZE, 810, sizeof(CDBOXSIZE))
odsmacro(CDEMBEDDEDEDITCTL, 816, sizeof(CDEMBEDDEDEDITCTL))
odsmacro(CDEMBEDDEDSCHEDCTLEXTRA,818,sizeof(CDEMBEDDEDSCHEDCTLEXTRA))
odsmacro(LOG_SEARCHR6_REQ, 821, sizeof(LOG_SEARCHR6_REQ))
odsmacro(CDBACKGROUNDPROPERTIES, 822, sizeof(CDBACKGROUNDPROPERTIES))
odsmacro(CDTEXTPROPERTY,833,sizeof(CDTEXTPROPERTY))
odsmacro(CDDATAFLAGS,834,sizeof(CDDATAFLAGS))
odsmacro(CDFILEHEADER, 835, sizeof(CDFILEHEADER))
odsmacro(CDFILESEGMENT, 836, sizeof(CDFILESEGMENT))
odsmacro(CDEVENTENTRY, 847, sizeof(CDEVENTENTRY))
odsmacro(CDACTIONEXT, 848, sizeof(CDACTIONEXT))
odsmacro(CDEMBEDDEDCALCTL, 849, sizeof(CDEMBEDDEDCALCTL))
odsmacro(CDTABLEDATAEXTENSION,857,sizeof(CDTABLEDATAEXTENSION))
odsmacro(CDLARGEPARAGRAPH, 909, sizeof(CDLARGEPARAGRAPH))
odsmacro(CDIGNORE, 912, sizeof(CDIGNORE))
odsmacro(VIEW_COLUMN_FORMAT5,914,sizeof(VIEW_COLUMN_FORMAT5))
odsmacro(CDEMBEDEXTRAINFO, 934, sizeof(CDEMBEDEXTRAINFO))
odsmacro(CDEMBEDDEDCONTACTLIST, 935, sizeof(CDEMBEDDEDCONTACTLIST))
**Sample Usage :**
```
void           *pItemValue;
CDFONTTABLE     cdFontTab;
CDFACE          cdFace;
WORD            wIndex;

/* RecordPtr points to the item value in canonical format after the
   datatype word. The item value starts with a CDFONTTABLE structure. 
   Call ODSReadMemory() to convert this CDFONTTABLE to host format and
   store it in cdFontTab. ODSReadMemory() advances pItemValue to
   point to the next byte in the input buffer after the CDFONTTABLE.
*/

pItemValue = RecordPtr;
ODSReadMemory( &pItemValue, _CDFONTTABLE, &cdFontTab, 1 );

for (wIndex = 0; wIndex < cdFontTab.Fonts; wIndex++)
{
    ODSReadMemory( &pItemValue, _CDFACE, &cdFace, 1 );
    printf( "    Font %d:\n", wIndex );
    printf( "       Face    = %d\n", cdFace.Face );
    printf( "       Family  = %d\n", cdFace.Family );
    printf( "       Name    = %s\n", cdFace.Name );
}
```
**See Also :**
[ODSReadMemory](D:/md_files/ODSReadMemory.md)
[ODSWriteMemory](D:/md_files/ODSWriteMemory.md)
[ODSLength](D:/md_files/ODSLength.md)
[NSFItemInfo](D:/md_files/NSFItemInfo.md)
[odsmacro](D:/md_files/odsmacro.md)
---
