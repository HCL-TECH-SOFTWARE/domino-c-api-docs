##### Data Type : Composite Data
##### CDBORDERINFO - Structure defining border information for a table.
---
##### #include <editods.h>
**Description :**
This CD record describes border information for a given table.  This CD record 
will be preceded with CD record CDPRETABLEBEGIN both encapsulated between a 
CDBEGINRECORD and a CDENDRECORD record with CD record signature CDPRETABLEBEGIN.

CDBEGINRECORD
	CDPRETABLEBEGIN
	 CDBORDERINFO
CDENDRECORD


WSIG   Header   Signature and length of this record
DWORD  Flags   Not Used must be 0
DWORD  BorderStyle  CDBORDERSTYLE_xxx
WORD   BorderWidthTop Thickness Top
WORD   BorderWidthLeft Thickness Left
WORD   BorderWidthBottom Thickness Bottom
WORD   BorderWidthRight Thickness Right
DWORD  dwSpare
WORD   BorderFlags  CDBORDER_FLAGS_xxx
WORD   DropShadowWidth Border Effects Drop Shadow Width
WORD   InnerWidthTop  Inside Thickness Top
WORD   InnerWidthLeft  Inside Thickness Left
WORD   InnerWidthBottom Inside Thickness Bottom
WORD   InnerWidthRight  Inside Thickness Right
WORD   OuterWidthTop  Outside Thickness Top
WORD   OuterWidthLeft  Outside Thickness Left
WORD   OuterWidthBottom Outside Thickness Bottom
WORD   OuterWidthRight Outside Thickness Right
COLOR_VALUE Color   Border Color
WORD   wSpares[5]



**See Also :**
[CDBORDERSTYLE_xxx](D:/md_files/CDBORDERSTYLE_xxx.md)
[CDBORDER_FLAGS_xxx](D:/md_files/CDBORDER_FLAGS_xxx.md)
[CDPRETABLEBEGIN](D:/md_files/CDPRETABLEBEGIN.md)
---
