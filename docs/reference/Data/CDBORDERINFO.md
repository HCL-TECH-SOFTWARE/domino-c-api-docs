##### Data Type : Composite Data
##### CDBORDERINFO - Structure defining border information for a table.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   WSIG Header; /* Signature and length of this record */
   DWORD       Flags;
   WORD        BorderStyle;
   WORD        BorderWidthTop; 
   WORD        BorderWidthLeft; 
   WORD        BorderWidthBottom; 
   WORD        BorderWidthRight; 
   DWORD       dwSpare;
   WORD        BorderFlags;
   WORD        DropShadowWidth;
   WORD        InnerWidthTop; 
   WORD        InnerWidthLeft; 
   WORD        InnerWidthBottom; 
   WORD        InnerWidthRight; 
   WORD        OuterWidthTop; 
   WORD        OuterWidthLeft; 
   WORD        OuterWidthBottom; 
   WORD        OuterWidthRight; 
   COLOR_VALUE Color;
   WORD        wSpares[5];
} CDBORDERINFO;
```

**Description :**

This CD record describes border information for a given table.  This CD record will be preceded with CD record CDPRETABLEBEGIN both encapsulated between a CDBEGINRECORD and a CDENDRECORD record with CD record signature CDPRETABLEBEGIN.<br>
<br>
CDBEGINRECORD<br>
	CDPRETABLEBEGIN<br>
		CDBORDERINFO<br>
CDENDRECORD<br>
<br>
<br>
WSIG			Header			Signature and length of this record<br>
DWORD		Flags			Not Used must be 0<br>
DWORD		BorderStyle		CDBORDERSTYLE_xxx<br>
WORD			BorderWidthTop	Thickness Top<br>
WORD			BorderWidthLeft	Thickness Left<br>
WORD			BorderWidthBottom	Thickness Bottom<br>
WORD			BorderWidthRight	Thickness Right<br>
DWORD		dwSpare<br>
WORD			BorderFlags		CDBORDER_FLAGS_xxx<br>
WORD			DropShadowWidth	Border Effects Drop Shadow Width<br>
WORD			InnerWidthTop		Inside Thickness Top<br>
WORD			InnerWidthLeft		Inside Thickness Left<br>
WORD			InnerWidthBottom	Inside Thickness Bottom<br>
WORD			InnerWidthRight		Inside Thickness Right<br>
WORD			OuterWidthTop		Outside Thickness Top<br>
WORD			OuterWidthLeft		Outside Thickness Left<br>
WORD			OuterWidthBottom	Outside Thickness Bottom<br>
WORD			OuterWidthRight	Outside Thickness Right<br>
COLOR_VALUE	Color			Border Color<br>
WORD			wSpares[5]<br>
<br>



**See Also :**
[CDBORDERSTYLE_xxx](/domino-c-api-docs/reference/Symb/CDBORDERSTYLE_xxx)
[CDBORDER_FLAGS_xxx](/domino-c-api-docs/reference/Symb/CDBORDER_FLAGS_xxx)
[CDPRETABLEBEGIN](/domino-c-api-docs/reference/Data/CDPRETABLEBEGIN)
---
