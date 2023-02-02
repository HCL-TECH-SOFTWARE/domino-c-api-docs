##### Data Type : Composite Data
##### CDEXT2FIELD - Extended field reference record used for currency and numeric symbol information.
---
##### #include <editods.h>
**Description :**
New field attributes have been added in Release 5.0 of Domino.  To preserve 
compatibility with existing applications, the new attributes have been placed 
in this second extension to the CDFIELD record.  This record will be  present 
in the $Body item of the form note for each field defined.

Header
	Numeric Symbol Data
NumSmyPref  Numeric Symbol Data preferences 
NumSymFlags  Reserved for future use
DecimalSymLength Decimal Symbol Length
MilliSepSymLength          Milli Separator Symbol Length 
NegativeSymLength Negative Symbol Length
MilliGroupSize  Number of digits per "thousands" group (i.e. where to put the 
"," in "1,000")
VerticalSpacing; Extra vertical spacing (%)
HorizontalSpacing; Extra horizontal spacing (%)
Unused2
FirstFieldLimitType  This value reflects the Only allow multiple choice in the 
Limit Input of the Rich Text Lite field,see FL_xxx
CurrencyPref  Currency Preferences
CurrencyType  Common or custom currency
CurrencyFlags  see NCURFMT_xxx
CurrencySymLength 
ISOCountry  ISO Country Code
Unused3
Unused4
	Date/Time Formatting Data
DTPref   Date/Time Preferences
DTFlags  see DT_xxx [DTFlags]
DTFlags2  see DT_xxx [DTFlags2]
DTDOWFmt  see DT_WFTM_xxx
DTYearFmt  see DT_YFMT_xxx
DTMonthFmt  see DT_MFMT_xxx
DTDayFmt  see DT_DFMT_xxx
DTDsep1Len  Length of first Date/Time Date separator
DTDsep2Len                     Length of second Date/Time Date separator
DTDsep3Len                     Length of third Date/Time Date separator
DTTsepLen                        Length of Date/Time Time separator
DTDShow  see DT_DSHOW_xxx
DTDSpecial  see DT_DSPEC_xxx
DTTShow  see DT_TSHOW_xxx
DTTZone  see TZFMT_xxx
Unused5
ECFlags  see EC_FLAG_WIDTH_PROPORTIONAL
Unused612
wCharacters  Number of characters if proportional width
wInputEnabledLen Input enabled formula.
wIMGroupFormulaLen Instant messaging buddy list group name. 

Since the $Body field has type TYPE_COMPOSITE, API programs that run on 
non-Intel architecture platforms must perform host/canonical conversion on 
CDEXT2FIELD records when accessing the $Body field of a form note.  

If there is variable numeric, currency and/or date/time data then the variable 
portion of the data will follow the fixed portion of this CD record in the 
preceding order. If you plan to use the date/time separators,you will need to 
declare the separator variables and assign values to their lengths (DTDsep1Len, 
DTDsep2Len, DTDsep3Len, DTTsepLen).

 The DT_STYLE_xxx flags are set using the DT_SET_STYLE function . The other 
DTFlags are set using an assignment statement.
 Example:    CDExt2Field.DTFlags = DT_SHOWDATE | DT_VALID; 
                          DT_SET_STYLE(CDExt2Field.DTFlags, DT_STYLE_DMY);

**See Also :**
[CDFIELD](D:/md_files/CDFIELD.md)
[DT_DFMT_xxx](D:/md_files/DT_DFMT_xxx.md)
[DT_DSHOW_xxx](D:/md_files/DT_DSHOW_xxx.md)
[DT_DSPEC_xxx](D:/md_files/DT_DSPEC_xxx.md)
[DT_MFMT_xxx](D:/md_files/DT_MFMT_xxx.md)
[DT_TSHOW_xxx](D:/md_files/DT_TSHOW_xxx.md)
[DT_WFMT_xxx](D:/md_files/DT_WFMT_xxx.md)
[DT_xxx [CDEXT2FIELD - DTFlags2]](D:/md_files/DT_xxx [CDEXT2FIELD - DTFlags2].md)
[DT_xxx [CDEXT2FIELD - DTFlags]](D:/md_files/DT_xxx [CDEXT2FIELD - DTFlags].md)
[DT_YFMT_xxx](D:/md_files/DT_YFMT_xxx.md)
[NCURFMT_xxx](D:/md_files/NCURFMT_xxx.md)
[NPREF_xxx](D:/md_files/NPREF_xxx.md)
[TZFMT_xxx](D:/md_files/TZFMT_xxx.md)
---
