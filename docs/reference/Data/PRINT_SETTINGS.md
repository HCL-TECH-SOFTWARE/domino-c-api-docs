##### Data Type : Rich Text
##### PRINT_SETTINGS - Print Settings
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
	WORD Flags;
#ifdef LITTLE_ENDIAN_ORDER
	#define PS_Initialized   0x0001 /* Print settings have been initialized 
*/
	#define PS_HeaderFooterOnFirst 0x0002 /* Print header/footer on first 
page */
	#define PS_CropMarks   0x0004 /* Print crop marks */
	#define PS_ChangeBin   0x0008 /* Paper source should be set for 1st & 
Other Pg. */
	#define PS_HeaderFooterRTL  0x0010 /* Paper source should be set for 
1st & Other Pg. */
	#define PS_ReleaseRightMargin  0x0020 /* Release the right margin when 
printing (to print into gutter) */
#else
	#define PS_Initialized   0x8000
	#define PS_HeaderFooterOnFirst 0x4000
	#define PS_CropMarks   0x2000
	#define PS_ChangeBin   0x1000
	#define PS_HeaderFooterRTL  0x0800 /* Paper source should be set for 
1st & Other Pg. */
	#define PS_ReleaseRightMargin  0x0400 /* Release the right margin when 
printing (to print into gutter) */
#endif

	WORD StartingPageNum;  /* Starting page number */
	WORD TopMargin;   /* Height between main body & top of page (TWIPS) */
	WORD BottomMargin;  /* Height between main body & bottom of page 
(TWIPS) */
	WORD ExtraLeftMargin;  /* Extra left margin width (TWIPS) */
	     /* (beyond whats already specified in document) */
	WORD ExtraRightMargin;  /* Extra right margin width (TWIPS) */
	     /* (beyond whats already specified in document) */
	WORD HeaderMargin;  /* Height between header & top of page (TWIPS) */
	WORD FooterMargin;  /* Height between footer & bottom of page (TWIPS) */
	WORD PageWidth;   /* Page width override (TWIPS) */
	     /* (0 = "use printer's page width") */
	WORD PageHeight;   /* Page height override (TWIPS) */
	     /* (0 = "use printer's page height") */
	WORD BinFirstPage;
	WORD BinOtherPage;
	WORD PageOrientation;  /* New in R6. 0 = undefined, 1 = Portrait, 2 = 
Landscape */
	WORD wSpare;   /* Spare word */
	DWORD spare[2];   /* (spare dwords) */
	} PRINT_SETTINGS;

**Description :**

Print settings passed to editor export procedures.<br>
<br>
Flags				Flags for print settings:		
<ul><br>
	PS_Initialized		Print settings have been initialized<br>
	PS_HeaderFooterOnFirst		Header and footer are printed on the first page<br>
	PS_CropMarks		Crop marks will be printed<br>
	PS_ChangeBin		Different paper bins will be used for the first page and all subsequent pages<br>
	PS_HeaderFooterRTL		Paper source should be set for 1st &amp; Other Pg.<br>
	PS_ReleaseRightMargin		Release the right margin when printing (to print into gutter)<br>
StartingPageNum	Page number of first page<br>
TopMargin	Height in &quot;twips&quot; (1/1440 inch) between top of page and main body<br>
BottomMargin	Height in twips between bottom of page and main body<br>
ExtraLeftMargin	Additional left margin space in twips (beyond what's already specified in the document)<br>
ExtraRightMargin	Additional right margin space in twips (beyond what's already specified in the document)<br>
HeaderMargin	Height in twips between top of page and header<br>
FooterMargin	Height in twips between bottom of page and footer<br>
PageWidth	If non-zero, override the printer's page width with this dimension (in twips)<br>
PageHeight	If non-zero, override the printer's page height with this dimension (in twips)<br>
BinFirstPage	Index of paper bin to use for the first page<br>
BinOtherPage	Index of paper bin to use for all other pages<br>
PageOrientation	New in Notes/Domino 6.  0 = Undefined, 1 = Portrait, 2 = Landscape. See PSPO_xxx<br>
wSpare			Spare word	<br>
spare[2]			Spare dwords</ul>



**See Also :**
[EDITEXPORTDATA](/domino-c-api-docs/reference/Data/EDITEXPORTDATA)
[PRINTNEW_SETTINGS](/domino-c-api-docs/reference/Data/PRINTNEW_SETTINGS)
[PSPO_xxx](/domino-c-api-docs/reference/Symb/PSPO_xxx)
[PS_xxx](/domino-c-api-docs/reference/Symb/PS_xxx)
---
