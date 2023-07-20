##### Data Type : Composite Data
##### CDEXT2FIELD - Extended field reference record used for currency and numeric symbol information.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
	WSIG Header;
	/* Numeric symbol data */
	BYTE NumSymPref;   /* NPREF_xxx */
	BYTE NumSymFlags;  /* NNUMSYM_xxx */
	DWORD DecimalSymLength;
	DWORD MilliSepSymLength;
	DWORD NegativeSymLength;
	WORD MilliGroupSize;
  SWORD VerticalSpacing; /* extra vertical spacing (%) */
	SWORD HorizontalSpacing; /* extra horizontal spacing (%) */
	WORD Unused2;
	WORD FirstFieldLimitType;
	/* Currency data */
	BYTE CurrencyPref;  /* NPREF_xxx */
	BYTE CurrencyType;  /* NCURFMT_xxx */
	BYTE CurrencyFlags;  /* NCURFMT_xxx */
	DWORD CurrencySymLength;
	DWORD ISOCountry; 
	WORD ThumbnailImageWidth;  /* Hannover Thumbnail support */
	WORD ThumbnailImageHeight;
	WORD wThumbnailImageFileNameLength;
	WORD wIMOnlineNameFormulaLen;
	/* Date/time formatting data */
	BYTE DTPref;    /* NPREF_xxx */
	DWORD DTFlags;   /* DT_xxx */
	DWORD DTFlags2;   /* DT_xxx */
	BYTE DTDOWFmt;   /* DT_WFMT_xxx */
	BYTE DTYearFmt;   /* DT_YFMT_xxx */
	BYTE DTMonthFmt;   /* DT_MFMT_xxx */
	BYTE DTDayFmt;   /* DT_DFMT_xxx */
	BYTE DTDsep1Len;
	BYTE DTDsep2Len;
	BYTE DTDsep3Len;
	BYTE DTTsepLen;
	BYTE DTDShow;   /* DT_DSHOW_xxx */
	BYTE DTDSpecial;   /* DT_DSPEC_xxx */
	BYTE DTTShow;   /* DT_TSHOW_xxx */
	BYTE DTTZone;   /* TZFMT_xxx */
	DWORD Unused5;
	/* Proportional font for fields data */

	BYTE ECFlags;
	BYTE Unused612;
	WORD wCharacters; /* Number of characters if proportional width */
	WORD wInputEnabledLen; /* Input enabled formula. */
	WORD wIMGroupFormulaLen; /* Instant messageing buddy list group name. */
	      /* Now comes the variable part of the struct... */
} CDEXT2FIELD;

```

**Description :**

New field attributes have been added in Release 5.0 of Domino.  To preserve compatibility with existing applications, the new attributes have been placed in this second extension to the CDFIELD record.  This record will be  present in the $Body item of the form note for each field defined.<br>
<br>
Header<br>
	<i>Numeric Symbol Data</i><br>
NumSmyPref		Numeric Symbol Data preferences	<br>
NumSymFlags		Reserved for future use<br>
DecimalSymLength	Decimal Symbol Length<br>
MilliSepSymLength          Milli Separator Symbol Length	<br>
NegativeSymLength	Negative Symbol Length<br>
MilliGroupSize		Number of digits per &quot;thousands&quot; group (i.e. where to put the &quot;,&quot; in &quot;1,000&quot;)<br>
VerticalSpacing;	Extra vertical spacing (%)<br>
HorizontalSpacing;	Extra horizontal spacing (%)<br>
Unused2<br>
FirstFieldLimitType  This value reflects the Only allow multiple choice in the Limit Input of the Rich Text Lite field,see FL_xxx<br>
CurrencyPref		Currency Preferences<br>
CurrencyType		Common or custom currency<br>
CurrencyFlags		see NCURFMT_xxx<br>
CurrencySymLength	<br>
ISOCountry		ISO Country Code<br>
Unused3<br>
Unused4<br>
	<i>Date/Time Formatting Data</i><br>
DTPref			Date/Time Preferences<br>
DTFlags		see DT_xxx [DTFlags]<br>
DTFlags2		see DT_xxx [DTFlags2]<br>
DTDOWFmt		see DT_WFTM_xxx<br>
DTYearFmt		see DT_YFMT_xxx<br>
DTMonthFmt		see DT_MFMT_xxx<br>
DTDayFmt		see DT_DFMT_xxx<br>
DTDsep1Len		Length of first Date/Time Date separator<br>
DTDsep2Len                     Length of second Date/Time Date separator<br>
DTDsep3Len                     Length of third Date/Time Date separator<br>
DTTsepLen                        Length of Date/Time Time separator<br>
DTDShow		see DT_DSHOW_xxx<br>
DTDSpecial		see DT_DSPEC_xxx<br>
DTTShow		see DT_TSHOW_xxx<br>
DTTZone		see TZFMT_xxx<br>
Unused5<br>
ECFlags		see EC_FLAG_WIDTH_PROPORTIONAL<br>
Unused612<br>
wCharacters		Number of characters if proportional width<br>
wInputEnabledLen	Input enabled formula.<br>
wIMGroupFormulaLen	Instant messaging buddy list group name. <br>
<br>
Since the $Body field has type TYPE_COMPOSITE, API programs that run on non-Intel architecture platforms must perform host/canonical conversion on CDEXT2FIELD records when accessing the $Body field of a form note.  <br>
<br>
If there is variable numeric, currency and/or date/time data then the variable portion of the data will follow the fixed portion of this CD record in the preceding order. If you plan to use the date/time separators,you will need to declare the separator variables and assign values to their lengths (DTDsep1Len, DTDsep2Len, DTDsep3Len, DTTsepLen).<br>
<br>
 The DT_STYLE_xxx flags are set using the DT_SET_STYLE function . The other DTFlags are set using an assignment statement.<br>
<i> Example:    </i>CDExt2Field.DTFlags = DT_SHOWDATE | DT_VALID; <br>
                          DT_SET_STYLE(CDExt2Field.DTFlags, DT_STYLE_DMY);


**See Also :**
[CDFIELD](/domino-c-api-docs/reference/Data/CDFIELD)
[DT_DFMT_xxx](/domino-c-api-docs/reference/Symb/DT_DFMT_xxx)
[DT_DSHOW_xxx](/domino-c-api-docs/reference/Symb/DT_DSHOW_xxx)
[DT_DSPEC_xxx](/domino-c-api-docs/reference/Symb/DT_DSPEC_xxx)
[DT_MFMT_xxx](/domino-c-api-docs/reference/Symb/DT_MFMT_xxx)
[DT_TSHOW_xxx](/domino-c-api-docs/reference/Symb/DT_TSHOW_xxx)
[DT_WFMT_xxx](/domino-c-api-docs/reference/Symb/DT_WFMT_xxx)
[DT_xxx [CDEXT2FIELD - DTFlags2]](/domino-c-api-docs/reference/Symb/DT_xxx [CDEXT2FIELD - DTFlags2])
[DT_xxx [CDEXT2FIELD - DTFlags]](/domino-c-api-docs/reference/Symb/DT_xxx [CDEXT2FIELD - DTFlags])
[DT_YFMT_xxx](/domino-c-api-docs/reference/Symb/DT_YFMT_xxx)
[NCURFMT_xxx](/domino-c-api-docs/reference/Symb/NCURFMT_xxx)
[NPREF_xxx](/domino-c-api-docs/reference/Symb/NPREF_xxx)
[TZFMT_xxx](/domino-c-api-docs/reference/Symb/TZFMT_xxx)
---
