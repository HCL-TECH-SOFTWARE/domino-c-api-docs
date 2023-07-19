##### Data Type : Rich Text
##### PRINTNEW_SETTINGS - New Print Settings
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
   WORD Flags;            /* PS_xxx */
   WORD StartingPageNum;  /* Starting page number */
   WORD TopMargin;        /* Height between body & page top */
   WORD BottomMargin;     /* Height between body & page bottom */
   WORD ExtraLeftMargin;  /* Extra left margin width (TWIPS) */
             /* (beyond whats already specified in document) */
   WORD ExtraRightMargin; /* Extra right margin width (TWIPS) */
             /* (beyond whats already specified in document) */
   WORD HeaderMargin;     /* Height between header & page top */
   WORD FooterMargin;     /* Height between footer & page bot. */
   WORD PageWidth;        /* Page width override (TWIPS) */
             /* (0 = "use printer's page width") */
   WORD PageHeight;       /* Page height override (TWIPS) */
             /* (0 = "use printer's page height") */
   WORD BinFirstPage;     /* Index of bin for 1st page */
   WORD BinOtherPage;     /* Index of bin for other pages */
   DWORD spare[3];        /* (spare words) */
} PRINTNEW_SETTINGS;

**Description :**

New print settings passed to editor export procedures.<br>
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
BinOtherPage	Index of paper bin to use for all other pages</ul>



**See Also :**
[PRINT_SETTINGS](/domino-c-api-docs/reference/Data/PRINT_SETTINGS)
[PS_xxx](/domino-c-api-docs/reference/Symb/PS_xxx)
---
