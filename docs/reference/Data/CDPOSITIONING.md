##### Data Type : Composite Data
##### CDPOSITIONING - Defines position information for a layer box. 
---
```
#include <editods.h>
```

**Definition :**

typedef struct
 {
 BSIG    Header;
 BYTE    Scheme;
 BYTE    bReserved;   /*  reserved for future use */
 LONG    ZIndex;
 LENGTH_VALUE Top;
 LENGTH_VALUE Left;
 LENGTH_VALUE Bottom;
 LENGTH_VALUE Right;   /*  not implemented */
	ALIGNED_NUMBER BrowserLeftOffset; /*  subtract from Top.Length to get 
left for a browser */
	ALIGNED_NUMBER BrowserRightOffset; /*  not implemented */
 } CDPOSITIONING;

**Description :**

This CD record contains position information for a layer box. The fields in this record are:
<ul><br>

<ul>Header			Signature and Length of this CD record.<br>
Scheme		See CDPOSITIONING_SCHEME_xxx. <b> </b><br>
bReserved		Reserved for future use.<br>
ZIndex			Controls the position of a layer in relation to other layers (in front of or behind them).<br>
Top			The upper position of a CDBOX in a layer.<br>
Left			The left position of a CDBOX in a layer.<br>
Bottom			The lower position of a CDBOX in a layer.<br>
Right			Not implemented.</ul>
</ul>
	BrowserLeftOffset  	Subtract from Top.Length to get left for a browser.<br>
	BrowserRightOffset	Not implemented.


**See Also :**
[CDBOXSIZE](/domino-c-api-docs/reference/Data/CDBOXSIZE)
[CDLAYER](/domino-c-api-docs/reference/Data/CDLAYER)
[CDPOSITIONING_SCHEME_xxx](/domino-c-api-docs/reference/Symb/CDPOSITIONING_SCHEME_xxx)
---
