##### Data Type : Rich Text
##### PRINTNEW_SETTINGS - New Print Settings
---
```
#include <editods.h>
```
**Description :**

New print settings passed to editor export procedures.
Flags    Flags for print settings:
	PS_Initialized  Print settings have been initialized
 PS_HeaderFooterOnFirst  Header and footer are printed on the first page
 PS_CropMarks  Crop marks will be printed
 PS_ChangeBin  Different paper bins will be used for the first page and all 
subsequent pages
	PS_HeaderFooterRTL  Paper source should be set for 1st & Other Pg.
	PS_ReleaseRightMargin  Release the right margin when printing (to print 
into gutter)
StartingPageNum Page number of first page
TopMargin Height in "twips" (1/1440 inch) between top of page and main body
BottomMargin Height in twips between bottom of page and main body
ExtraLeftMargin Additional left margin space in twips (beyond what's already 
specified in the document)
ExtraRightMargin Additional right margin space in twips (beyond what's already 
specified in the document)
HeaderMargin Height in twips between top of page and header
FooterMargin Height in twips between bottom of page and footer
PageWidth If non-zero, override the printer's page width with this dimension 
(in twips)
PageHeight If non-zero, override the printer's page height with this dimension 
(in twips)
BinFirstPage Index of paper bin to use for the first page
BinOtherPage Index of paper bin to use for all other pages

**See Also :**
[PRINT_SETTINGS](/domino-c-api-docs/reference/Data/PRINT_SETTINGS)
[PS_xxx](/domino-c-api-docs/reference/Symb/PS_xxx)
---
