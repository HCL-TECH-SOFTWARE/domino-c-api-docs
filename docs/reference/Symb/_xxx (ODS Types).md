##### Symbolic Value : Canonical Format Conversion
##### _xxx (ODS Types) - Identifies the Domino data structure to ODS functions.
---
```
#include <odstypes.h>
```

**Symbolic Values :**

	_xxx	  -  ODS Type symbols that identify Domino data structures. The symbol is just the Domino data structure name prefixed with an underscore. See Description for the complete list of all ODS type symbols.


**Description :**

You must specify one of these symbols as the type input to ODSLength, ODSReadMemory, and ODSWriteMemory.<br>
<br>
You must call ODSReadMemory to convert data structures from Domino canonical format to machine-specific (host) format, and ODSWriteMemory to convert a data structure from host format to Domino canonical format.<br>
<br>
Your API program must perform this conversion if (1) it runs on non-Intel architecture machines, and (2) it is reading or writing item data of one of the following data types:<br>
<tt><font size="2"><br>
 &nbsp; &nbsp;TYPE_COMPOSITE<br>
 &nbsp; &nbsp;TYPE_COLLATION<br>
 &nbsp; &nbsp;TYPE_OBJECT<br>
 &nbsp; &nbsp;TYPE_VIEW_FORMAT<br>
 &nbsp; &nbsp;TYPE_ICON<br>
 &nbsp; &nbsp;TYPE_SIGNATURE<br>
 &nbsp; &nbsp;TYPE_SEAL<br>
 &nbsp; &nbsp;TYPE_SEALDATA<br>
 &nbsp; &nbsp;TYPE_SEAL_LIST<br>
 &nbsp; &nbsp;TYPE_WORKSHEET_DATA<br>
 &nbsp; &nbsp;TYPE_USERDATA</font></tt>
<ul><br>
<tt>&nbsp; &nbsp; TYPE_QUERY</tt><br>
<tt>&nbsp; &nbsp; TYPE_ACTION</tt><br>
<tt>&nbsp; &nbsp; TYPE_ASSISTANT_INFO</tt><br>
<tt>&nbsp; &nbsp; TYPE_VIEWMAP_DATASET</tt><br>
<tt>&nbsp; &nbsp; TYPE_VIEWMAP_LAYOUT</tt><br>
<tt>&nbsp; &nbsp; </tt><tt>TYPE_CALENDAR_FORMAT</tt><br>
<br>
Your API program must not perform conversion when accessing items of any other data type, or when accessing non-item data (Domino and Notes automatically performs the conversion for you in these cases).<br>
<br>
From ods.h:<br>
<tt><font size="2">/* Base ODS types */<br>
<br>
#define _SHORT 0<br>
#define _USHORT _SHORT<br>
#define _WORD _SHORT<br>
#define _STATUS _SHORT</font></tt><br>
<tt><font size="2">#define _UNICODE _SHORT<br>
#define _LONG 1<br>
#define _FLOAT 2<br>
#define _DWORD _LONG<br>
#define _ULONG _LONG<br>
<br>
/* ODS types that are the size of a base type */<br>
<br>
#define _NUMBER _FLOAT<br>
#define _NOTEID _LONG<br>
<br>
/* Include the rest of the ODS types from odstypes.h */<br>
<br>
#if defined(GCC) &amp;&amp; defined(SUN)<br>
#define odsmacro(name, num, size) enum{_/*##*/name = num};<br>
#else<br>
#define odsmacro(name, num, size) enum{_##name = num};<br>
#endif<br>
#include &quot;odstypes.h&quot;<br>
#undef odsmacro</font></tt><br>
<br>
<br>
From odstypes.h:<br>
<tt><font size="2">odsmacro(TIMEDATE,10,sizeof(TIMEDATE))<br>
odsmacro(TIMEDATE_PAIR,11,sizeof(TIMEDATE_PAIR))</font></tt><br>
<tt><font size="2">odsmacro(ALIGNED_NUMBER_PAIR,12,sizeof(ALIGNED_NUMBER_PAIR))<br>
odsmacro(LIST,13,sizeof(LIST))<br>
odsmacro(RANGE,14,sizeof(RANGE))<br>
odsmacro(DBID,15,sizeof(DBID))<br>
odsmacro(ITEM,17,sizeof(ITEM))<br>
odsmacro(ITEM_TABLE,18,sizeof(ITEM_TABLE))<br>
odsmacro(SEARCH_MATCH,24,sizeof(SEARCH_MATCH))<br>
odsmacro(ORIGINATORID,26,sizeof(ORIGINATORID))<br>
#define _OID _ORIGINATORID<br>
odsmacro(OBJECT_DESCRIPTOR,27,sizeof(OBJECT_DESCRIPTOR))<br>
odsmacro(UNIVERSALNOTEID,28,sizeof(UNIVERSALNOTEID))<br>
#define _UNID _UNIVERSALNOTEID<br>
odsmacro(VIEW_TABLE_FORMAT,29,sizeof(VIEW_TABLE_FORMAT))<br>
odsmacro(VIEW_COLUMN_FORMAT,30,sizeof(VIEW_COLUMN_FORMAT))<br>
odsmacro(NOTELINK,33,sizeof(NOTELINK))<br>
odsmacro(LICENSEID,34,sizeof(LICENSEID))<br>
odsmacro(VIEW_FORMAT_HEADER,42,sizeof(VIEW_FORMAT_HEADER))<br>
odsmacro(VIEW_TABLE_FORMAT2,43,sizeof(VIEW_TABLE_FORMAT2))<br>
odsmacro(DBREPLICAINFO,56,sizeof(DBREPLICAINFO))<br>
odsmacro(FILEOBJECT,58,sizeof(FILEOBJECT))<br>
odsmacro(COLLATION,59,sizeof(COLLATION))<br>
odsmacro(COLLATE_DESCRIPTOR,60,sizeof(COLLATE_DESCRIPTOR))<br>
odsmacro(CDKEYWORD,68,sizeof(CDKEYWORD))<br>
odsmacro(CDLINK2,72,sizeof(CDLINK2))<br>
odsmacro(CDLINKEXPORT2,97,sizeof(CDLINKEXPORT2))<br>
odsmacro(CDPARAGRAPH,109,sizeof(CDPARAGRAPH))<br>
odsmacro(CDPABDEFINITION,110,sizeof(CDPABDEFINITION))<br>
odsmacro(CDPABREFERENCE,111,sizeof(CDPABREFERENCE))<br>
odsmacro(CDFIELD_PRE_36,112,sizeof(CDFIELD_PRE_36))<br>
odsmacro(CDTEXT,113,sizeof(CDTEXT))<br>
odsmacro(CDDOCUMENT,114,sizeof(CDDOCUMENT))<br>
odsmacro(CDMETAFILE,115,sizeof(CDMETAFILE))<br>
odsmacro(CDBITMAP,116,sizeof(CDBITMAP))<br>
odsmacro(CDHEADER,117,sizeof(CDHEADER))<br>
odsmacro(CDFIELD,118,sizeof(CDFIELD))<br>
odsmacro(CDFONTTABLE,119,sizeof(CDFONTTABLE))<br>
odsmacro(CDFACE,120,sizeof(CDFACE))<br>
odsmacro(CDCGM,156,sizeof(CDCGM))<br>
odsmacro(CDTIFF,159,sizeof(CDTIFF))<br>
odsmacro(CDBITMAPHEADER,162,sizeof(CDBITMAPHEADER))<br>
odsmacro(CDBITMAPSEGMENT,163,sizeof(CDBITMAPSEGMENT))<br>
odsmacro(CDCOLORTABLE,164,sizeof(CDCOLORTABLE))<br>
odsmacro(CDPATTERNTABLE,165,sizeof(CDPATTERNTABLE))<br>
odsmacro(CDGRAPHIC,166,sizeof(CDGRAPHIC))<br>
odsmacro(CDPMMETAHEADER,167,sizeof(CDPMMETAHEADER))<br>
odsmacro(CDWINMETAHEADER,168,sizeof(CDWINMETAHEADER))<br>
odsmacro(CDMACMETAHEADER,169,sizeof(CDMACMETAHEADER))<br>
odsmacro(CDCGMMETA,170,sizeof(CDCGMMETA))<br>
odsmacro(CDPMMETASEG,171,sizeof(CDPMMETASEG))<br>
odsmacro(CDWINMETASEG,172,sizeof(CDWINMETASEG))<br>
odsmacro(CDMACMETASEG,173,sizeof(CDMACMETASEG))<br>
odsmacro(CDDDEBEGIN,174,BIGGERTHANABYTE)<br>
odsmacro(CDDDEEND,175,sizeof(CDDDEEND))<br>
odsmacro(CDTABLEBEGIN,176,sizeof(CDTABLEBEGIN))<br>
odsmacro(CDTABLECELL,177,sizeof(CDTABLECELL))<br>
odsmacro(CDTABLEEND,178,sizeof(CDTABLEEND))<br>
odsmacro(CDSTYLENAME,188,sizeof(CDSTYLENAME))<br>
odsmacro(FILEOBJECT_MACEXT,192,sizeof(FILEOBJECT_MACEXT))<br>
odsmacro(FILEOBJECT_HPFSEXT,193,sizeof(FILEOBJECT_HPFSEXT))<br>
odsmacro(CDOLEBEGIN,218,sizeof(CDOLEBEGIN))<br>
odsmacro(CDOLEEND,219,sizeof(CDOLEEND))<br>
odsmacro(CDHOTSPOTBEGIN,230,sizeof(CDHOTSPOTBEGIN))<br>
odsmacro(CDHOTSPOTEND,231,sizeof(CDHOTSPOTEND))<br>
odsmacro(CDBUTTON, 237, sizeof (CDBUTTON))</font></tt><br>
<tt><font size="2">odsmacro(CDBAR, 308, sizeof(CDBAR))<br>
odsmacro(CDQUERYHEADER,314,sizeof(CDQUERYHEADER))<br>
odsmacro(CDQUERYTEXTTERM,315,sizeof(CDQUERYTEXTTERM))<br>
odsmacro(CDACTIONHEADER,316,sizeof(CDACTIONHEADER))<br>
odsmacro(CDACTIONMODIFYFIELD,317,sizeof(CDACTIONMODIFYFIELD))<br>
odsmacro(ODS_ASSISTSTRUCT,318,sizeof(ODS_ASSISTSTRUCT))<br>
odsmacro(VIEWMAP_HEADER_RECORD,319,sizeof(VIEWMAP_HEADER_RECORD))<br>
odsmacro(VIEWMAP_RECT_RECORD,320,sizeof(VIEWMAP_RECT_RECORD))<br>
odsmacro(VIEWMAP_BITMAP_RECORD,321,sizeof(VIEWMAP_BITMAP_RECORD))<br>
odsmacro(VIEWMAP_REGION_RECORD,322,sizeof(VIEWMAP_REGION_RECORD))<br>
odsmacro(VIEWMAP_POLYGON_RECORD,323,sizeof(VIEWMAP_POLYGON_RECORD))<br>
odsmacro(VIEWMAP_POLYLINE_RECORD,324,sizeof(VIEWMAP_POLYLINE_RECORD)<br>
odsmacro(VIEWMAP_ACTION_RECORD,325,sizeof(VIEWMAP_ACTION_RECORD))<br>
odsmacro(ODS_ASSISTRUNINFO,326,sizeof(ODS_ASSISTRUNINFO))<br>
odsmacro(CDACTIONREPLY,327,sizeof(CDACTIONREPLY))<br>
odsmacro(CDACTIONFORMULA,332,sizeof(CDACTIONFORMULA))<br>
odsmacro(CDACTIONLOTUSSCRIPT,333,sizeof(CDACTIONLOTUSSCRIPT))<br>
odsmacro(CDQUERYBYFIELD,334,sizeof(CDQUERYBYFIELD))</font></tt><br>
<tt><font size="2">odsmacro(CDACTIONSENDMAIL,335,sizeof(CDACTIONSENDMAIL))<br>
odsmacro(CDACTIONDBCOPY,336,sizeof(CDACTIONDBCOPY))<br>
odsmacro(CDACTIONDELETE,337,sizeof(CDACTIONDELETE))<br>
odsmacro(CDACTIONBYFORM,338,sizeof(CDACTIONBYFORM))</font></tt><br>
<tt><font size="2">odsmacro(ODS_ASSISTFIELDSTRUCT,339,sizeof(ODS_ASSISTFIELDSTRUCT))<br>
odsmacro(CDACTION, 340, sizeof(CDACTION))<br>
odsmacro(CDACTIONREADMARKS,341,sizeof(CDACTIONREADMARKS))<br>
odsmacro(CDEXTFIELD,342,sizeof(CDEXTFIELD))<br>
odsmacro(CDLAYOUT,343,sizeof(CDLAYOUT))<br>
odsmacro(CDLAYOUTTEXT,344,sizeof(CDLAYOUTTEXT))<br>
odsmacro(CDLAYOUTEND,345,sizeof(CDLAYOUTEND))<br>
odsmacro(CDLAYOUTFIELD,346,sizeof(CDLAYOUTFIELD))<br>
odsmacro(VIEWMAP_DATASET_RECORD,347,BIGGERTHANABYTE)<br>
odsmacro(CDDOCAUTOLAUNCH,350,sizeof(CDDOCAUTOLAUNCH))<br>
odsmacro(CDPABHIDE, 358, sizeof(CDPABHIDE))<br>
odsmacro(CDPABFORMULAREF, 359, sizeof(CDPABFORMULAREF))<br>
odsmacro(CDACTIONBAR, 360, sizeof(CDACTIONBAR))<br>
odsmacro(CDACTIONFOLDER,361,sizeof(CDACTIONFOLDER))<br>
odsmacro(CDACTIONNEWSLETTER,362,sizeof(CDACTIONNEWSLETTER))<br>
odsmacro(CDACTIONRUNAGENT,363,sizeof(CDACTIONRUNAGENT))<br>
odsmacro(CDACTIONSENDDOCUMENT,364,sizeof(CDACTIONSENDDOCUMENT))<br>
odsmacro(CDQUERYFORMULA,365,sizeof(CDQUERYFORMULA))<br>
odsmacro(CDQUERYBYFORM,373,sizeof(CDQUERYBYFORM))<br>
odsmacro(ODS_ASSISTRUNOBJECTHEADER,374,sizeof(ODS_ASSISTRUNOBJECTHEADER))</font></tt><br>
<tt><font size="2">odsmacro(ODS_ASSISTRUNOBJECTENTRY,375,sizeof(ODS_ASSISTRUNOBJECTENTRY))<br>
odsmacro(CDLAYOUTGRAPHIC,407,sizeof(CDLAYOUTGRAPHIC))</font></tt><br>
<tt><font size="2">odsmacro(CDQUERYBYFOLDER,413,sizeof(CDQUERYBYFOLDER))<br>
odsmacro(CDQUERYUSESFORM,423,sizeof(CDQUERYUSESFORM))<br>
odsmacro(VIEW_COLUMN_FORMAT2, 428, sizeof(VIEW_COLUMN_FORMAT2))<br>
odsmacro(VIEWMAP_TEXT_RECORD,464,sizeof(VIEWMAP_TEXT_RECORD))<br>
odsmacro(CDLAYOUTBUTTON,466,sizeof(CDLAYOUTBUTTON))<br>
odsmacro(CDQUERYTOPIC,471,sizeof(CDQUERYTOPIC))<br>
odsmacro(CDLSOBJECT,482,sizeof(CDLSOBJECT))<br>
odsmacro(CDHTMLHEADER,492,sizeof(CDHTMLHEADER))<br>
odsmacro(CDHTMLSEGMENT,493,sizeof(CDHTMLSEGMENT))odsmacro(SCHED_LIST,502,sizeof(SCHED_LIST))<br>
#define _SCHED_LIST_OBJ _SCHED_LIST<br>
odsmacro(SCHED_ENTRY,503,sizeof(SCHED_ENTRY))<br>
odsmacro(SCHEDULE,504,sizeof(SCHEDULE))<br>
odsmacro(CDTEXTEFFECT,508,sizeof(CDTEXTEFFECT))</font></tt><br>
<tt><font size="2">odsmacro(VIEW_CALENDAR_FORMAT,513,sizeof(VIEW_CALENDAR_FORMAT))<br>
odsmacro(CDSTORAGELINK,515,sizeof(CDSTORAGELINK))<br>
odsmacro(ACTIVEOBJECT,516,sizeof(ACTIVEOBJECT))<br>
odsmacro(ACTIVEOBJECTPARAM,517,sizeof(ACTIVEOBJECTPARAM))<br>
odsmacro(ACTIVEOBJECTSTORAGELINK,518,sizeof(ACTIVEOBJECTSTORAGELINK))odsmacro(CDTRANSPARENTTABLE,541,sizeof(CDTRANSPARENTTABLE))</font></tt><br>
<tt><font size="2">/* modified viewmap records, changed CD record from byte to word */<br>
odsmacro(VIEWMAP_POLYGON_RECORD,551,sizeof(VIEWMAP_POLYGON_RECORD))<br>
odsmacro(VIEWMAP_POLYLINE_RECORD,552,sizeof(VIEWMAP_POLYLINE_RECORD))</font></tt><br>
<tt><font size="2">odsmacro(SCHED_DETAIL_LIST,553,sizeof(SCHED_DETAIL_LIST))<br>
odsmacro(CDALTERNATEBEGIN,554,sizeof(CDALTERNATEBEGIN))<br>
odsmacro(CDALTERNATEEND,555,sizeof(CDALTERNATEEND))<br>
odsmacro(CDOLERTMARKER,556,sizeof(CDOLERTMARKER))<br>
odsmacro(HSOLERICHTEXT,557,sizeof(HSOLERICHTEXT))</font></tt><br>
<tt><font size="2">odsmacro(CDANCHOR, 559, sizeof(CDANCHOR))<br>
odsmacro(CDHRULE, 560, sizeof (CDHRULE))<br>
odsmacro(CDALTTEXT, 561, sizeof(CDALTTEXT))<br>
odsmacro(CDACTIONJAVAAGENT,562,sizeof(CDACTIONJAVAAGENT))<br>
odsmacro(CDHTMLBEGIN, 564, sizeof(CDHTMLBEGIN))<br>
odsmacro(CDHTMLEND, 565, sizeof(CDHTMLEND))<br>
odsmacro(CDHTMLFORMULA, 566, sizeof(CDHTMLFORMULA))</font></tt><br>
<tt><font size="2">odsmacro(CDBEGINRECORD, 577, sizeof (CDBEGINRECORD))</font></tt><br>
<tt><font size="2">odsmacro(CDENDRECORD, 578, sizeof (CDENDRECORD))</font></tt><br>
<tt><font size="2">odsmacro(CDVERTICALALIGN, 579, sizeof (CDVERTICALALIGN))</font></tt><br>
<tt><font size="2">odsmacro(CDFLOAT, 580, sizeof (CDFLOAT))</font></tt><br>
<tt><font size="2">odsmacro(CDTIMERINFO, 581, sizeof (CDTIMERINFO))</font></tt><br>
<tt><font size="2">odsmacro(CDTABLEROWHEIGHT, 582, sizeof (CDTABLEROWHEIGHT))</font></tt><br>
<tt><font size="2">odsmacro(CDTABLELABEL, 583, sizeof (CDTABLELABEL))</font></tt><br>
<tt><font size="2">odsmacro(CDTRANSITION, 610, sizeof (CDTRANSITION))</font></tt><br>
<tt><font size="2">odsmacro(CDPLACEHOLDER, 611, sizeof (CDPLACEHOLDER))</font></tt><br>
<tt><font size="2">odsmacro(CDEMBEDDEDVIEW, 615, sizeof (CDEMBEDDEDVIEW))</font></tt><br>
<tt><font size="2">odsmacro(CDEMBEDDEDOUTLINE, 620, BIGGERTHANABYTE)</font></tt><br>
<tt><font size="2">odsmacro(CDREGIONBEGIN, 621, sizeof(CDREGIONBEGIN))</font></tt><br>
<tt><font size="2">odsmacro(CDREGIONEND, 622, sizeof(CDREGIONEND))</font></tt><br>
<tt><font size="2">odsmacro(CDCELLBACKGROUNDDATA, 623, sizeof (CDCELLBACKGROUNDDATA))</font></tt><br>
<tt><font size="2">odsmacro(FRAMESETLENGTH, 625, sizeof(FRAMESETLENGTH))</font></tt><br>
<tt><font size="2">odsmacro(CDFRAMESETHEADER, 626, sizeof(CDFRAMESETHEADER))</font></tt><br>
<tt><font size="2">odsmacro(CDFRAMESET, 627, sizeof(CDFRAMESET))</font></tt><br>
<tt><font size="2">odsmacro(CDFRAME, 628, sizeof(CDFRAME))</font></tt><br>
<tt><font size="2">odsmacro(CDTARGET, 629, sizeof(CDTARGET))</font></tt><br>
<tt><font size="2">odsmacro(CDRESOURCE, 631, sizeof(CDRESOURCE))</font></tt><br>
<tt><font size="2">odsmacro(CDMAPELEMENT, 632, sizeof(CDMAPELEMENT))</font></tt><br>
<tt><font size="2">odsmacro(CDAREAELEMENT, 633, sizeof(CDAREAELEMENT))</font></tt><br>
<tt><font size="2">odsmacro(CDRECT, 634, sizeof(CDRECT))</font></tt><br>
<tt><font size="2">odsmacro(CDPOINT, 635, sizeof(CDPOINT))</font></tt><br>
<tt><font size="2">odsmacro(CDEMBEDDEDCTL, 636, sizeof (CDEMBEDDEDCTL))</font></tt><br>
<tt><font size="2">odsmacro(CDEVENT, 637, sizeof(CDEVENT))</font></tt><br>
<tt><font size="2">odsmacro(MIME_PART, 639, sizeof(MIME_PART))</font></tt><br>
<tt><font size="2">odsmacro(CDPRETABLEBEGIN,640,sizeof(CDPRETABLEBEGIN))</font></tt><br>
<tt><font size="2">odsmacro(CDCOLOR,645,sizeof(CDCOLOR))</font></tt><br>
<tt><font size="2">odsmacro(CDBORDERINFO, 646, sizeof (CDBORDERINFO))</font></tt><br>
<tt><font size="2">odsmacro(CDEXT2FIELD,672,sizeof(CDEXT2FIELD))</font></tt><br>
<tt><font size="2">odsmacro(CDEMBEDDEDSCHEDCTL, 674, sizeof(CDEMBEDDEDSCHEDCTL))</font></tt><br>
<tt><font size="2">odsmacro(RFC822ITEMDESC,675,sizeof(RFC822ITEMDESC))</font></tt><br>
<tt><font size="2">odsmacro(COLOR_VALUE,690,sizeof(COLOR_VALUE))</font></tt><br>
<tt><font size="2">odsmacro(CDBLOBPART,695,sizeof(CDBLOBPART))</font></tt><br>
<tt><font size="2">odsmacro(CDIMAGEHEADER, 705, sizeof(CDIMAGEHEADER))</font></tt><br>
<tt><font size="2">odsmacro(CDIMAGESEGMENT, 706, sizeof(CDIMAGESEGMENT))</font></tt><br>
<tt><font size="2">odsmacro(VIEW_TABLE_FORMAT3, 707, sizeof(VIEW_TABLE_FORMAT3))</font></tt><br>
<tt><font size="2">odsmacro(CDIDNAME, 708, sizeof(CDIDNAME))</font></tt><br>
<tt><font size="2">odsmacro(CDACTIONBAREXT,719,sizeof(CDACTIONBAREXT))</font></tt><br>
<tt><font size="2">odsmacro(CDLINKCOLORS,722,sizeof(CDLINKCOLORS))</font></tt><br>
<tt><font size="2">odsmacro(CDCAPTION,728,sizeof(CDCAPTION))</font></tt><br>
<tt><font size="2">odsmacro(CDFIELDHINT,742,sizeof(CDFIELDHINT))</font></tt><br>
<tt><font size="2">odsmacro(CDLSOBJECT_R6,744,sizeof(CDLSOBJECT_R6))</font></tt><br>
<tt><font size="2">odsmacro(CDINLINE, 756, sizeof(CDINLINE))</font></tt><br>
<tt><font size="2">odsmacro(CDTEXTPROPERTIESTABLE,765,sizeof(CDTEXTPROPERTIESTABLE))<br>
odsmacro(CDSPANRECORD,766,sizeof(CDSPANRECORD))<br>
odsmacro(CDDECSFIELD, 767, sizeof(CDDECSFIELD))<br>
odsmacro(CDLAYER, 808, sizeof(CDLAYER))<br>
odsmacro(CDPOSITIONING, 809, sizeof(CDPOSITIONING))</font></tt><br>
<tt><font size="2">odsmacro(CDBOXSIZE, 810, sizeof(CDBOXSIZE))</font></tt><br>
<tt><font size="2">odsmacro(CDEMBEDDEDEDITCTL, 816, sizeof(CDEMBEDDEDEDITCTL))<br>
odsmacro(CDEMBEDDEDSCHEDCTLEXTRA,818,sizeof(CDEMBEDDEDSCHEDCTLEXTRA))<br>
odsmacro(LOG_SEARCHR6_REQ, 821, sizeof(LOG_SEARCHR6_REQ))<br>
odsmacro(CDBACKGROUNDPROPERTIES, 822, sizeof(CDBACKGROUNDPROPERTIES))</font></tt><br>
<tt><font size="2">odsmacro(CDTEXTPROPERTY,833,sizeof(CDTEXTPROPERTY))<br>
odsmacro(CDDATAFLAGS,834,sizeof(CDDATAFLAGS))</font></tt><br>
<tt><font size="2">odsmacro(CDFILEHEADER, 835, sizeof(CDFILEHEADER))<br>
odsmacro(CDFILESEGMENT, 836, sizeof(CDFILESEGMENT))<br>
odsmacro(CDEVENTENTRY, 847, sizeof(CDEVENTENTRY))<br>
odsmacro(CDACTIONEXT, 848, sizeof(CDACTIONEXT))<br>
odsmacro(CDEMBEDDEDCALCTL, 849, sizeof(CDEMBEDDEDCALCTL))</font></tt><br>
<tt><font size="2">odsmacro(CDTABLEDATAEXTENSION,857,sizeof(CDTABLEDATAEXTENSION))<br>
odsmacro(CDLARGEPARAGRAPH, 909, sizeof(CDLARGEPARAGRAPH))<br>
odsmacro(CDIGNORE, 912, sizeof(CDIGNORE))</font></tt><br>
<tt><font size="2">odsmacro(VIEW_COLUMN_FORMAT5,914,sizeof(VIEW_COLUMN_FORMAT5))</font></tt><br>
<tt><font size="2">odsmacro(CDEMBEDEXTRAINFO, 934, sizeof(CDEMBEDEXTRAINFO))</font></tt><tt><font size="2"><br>
odsmacro(CDEMBEDDEDCONTACTLIST, 935, sizeof(CDEMBEDDEDCONTACTLIST))</font></tt></ul>



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
[ODSReadMemory](/domino-c-api-docs/reference/Func/ODSReadMemory)
[ODSWriteMemory](/domino-c-api-docs/reference/Func/ODSWriteMemory)
[ODSLength](/domino-c-api-docs/reference/Func/ODSLength)
[NSFItemInfo](/domino-c-api-docs/reference/Func/NSFItemInfo)
[odsmacro](/domino-c-api-docs/reference/Func/odsmacro)
---
