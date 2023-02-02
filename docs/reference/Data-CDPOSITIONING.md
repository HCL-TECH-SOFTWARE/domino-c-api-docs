##### Data Type : Composite Data
##### CDPOSITIONING - Defines position information for a layer box. 
---
##### #include <editods.h>
**Description :**
This CD record contains position information for a layer box. The fields in 
this record are:

Header   Signature and Length of this CD record.
Scheme  See CDPOSITIONING_SCHEME_xxx.  
bReserved  Reserved for future use.
ZIndex   Controls the position of a layer in relation to other layers (in front 
of or behind them).
Top   The upper position of a CDBOX in a layer.
Left   The left position of a CDBOX in a layer.
Bottom   The lower position of a CDBOX in a layer.
Right   Not implemented.
	BrowserLeftOffset   Subtract from Top.Length to get left for a browser.
	BrowserRightOffset Not implemented.

**See Also :**
[CDBOXSIZE](D:/md_files/CDBOXSIZE.md)
[CDLAYER](D:/md_files/CDLAYER.md)
[CDPOSITIONING_SCHEME_xxx](D:/md_files/CDPOSITIONING_SCHEME_xxx.md)
---
