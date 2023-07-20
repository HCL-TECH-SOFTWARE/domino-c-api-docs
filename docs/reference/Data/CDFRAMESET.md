##### Data Type : Composite Data
##### CDFRAMESET - Used to specify an HTML FRAMESET element
---
```
#include <fsods.h>
```

**Definition :**
```
typedef struct
	{
	WSIG Header;
	DWORD Flags;     /* fFSxxxxxxx as defined below. Unused bits must be 
set to 0 */
#define fFSBorderEnable   0x00000001 /* Set if BorderEnable is specified */
#define fFSFrameBorderDims   0x00000004 /* Set if FrameBorderWidth is specified 
*/
#define fFSFrameSpacingDims  0x00000008 /* Set if FrameSpacingWidth is 
specified */
#define fFSFrameBorderColor  0x00000040 /* Set if FrameBorderColor is specified 
*/
	BYTE  BorderEnable;    /* Specifies the HTML FRAMEBORDER attribute for 
this frameset element */
	BYTE  byAvail1;     /* Reserved for future use, must be 0 */
	WORD Reserved1;     /* Reserved for future use, must be 0 */
	WORD Reserved2;     /* Reserved for future use, must be 0 */
	WORD FrameBorderWidth;   /* Specifies the HTML BORDER attribute for 
this frameset element */
	WORD Reserved3;     /* Reserved for future use, must be 0 */
	WORD FrameSpacingWidth;   /* Specifies the HTML FRAMESPACING attribute 
for this frameset element */
	WORD Reserved4;     /* Reserved for future use, must be 0 */
	COLOR_VALUE ReservedColor1;  /* Reserved for future use, must be 0 */
	COLOR_VALUE ReservedColor2;  /* Reserved for future use, must be 0 */
/* RowQty and ColQty specify the number of FRAMESETLENGTH structures that follow
 * in the variable length data area.  Only one of these values can be non-zero,
 * meaning that a frameset will consist of all rows or all columns but never 
both. */
	WORD  RowQty; 
	WORD  ColQty;
	WORD  Reserved5;    /* Reserved for future use, must be 0 */
	WORD  Reserved6;    /* Reserved for future use, must be 0 */
	COLOR_VALUE FrameBorderColor; /* Used to specify the BORDERCOLOR 
attribute for this frameset element */
	BYTE  ThemeSetting;    /* Theme Setting */
	BYTE  Reserved7;       /* Reserved for future use, must be 0 */
	/* Variable length data follows (strings not null terminated)
	 * - Row FRAMESETLENGTH structures (count equals RowQty)
	 * - Col FRAMESETLENGTH structures (count equals ColQty) */
	} CDFRAMESET;

```

**Description :**

Header
<ul><br>
Flags			see fFSxxx<br>
BorderEnable		HTML FRAMEBORDER attribute<br>
byAvail1			reserved, must be 0<br>
Reserved1			reserved, must be 0<br>
FrameBorderWidth		HTML BORDER attribute<br>
Reserved3			reserved, must be 0<br>
FrameSpacingWidth	HTML FRAMESPACING attribute<br>
Reserved4			reserved, must be 0<br>
ReservedColor1		reserved for future use<br>
ReservedColor2		reserved for future use<br>
RowQty			The number of FRAMESETLENGTH structures defining row information.<br>
ColQty			The number of FRAMESETLENGTH structures defining column information.<br>
Reserved5			reserved, must be 0<br>
Reserved6			reserved, must be 0<br>
FrameBorderColor		HTML BORDERCOLOR attribute, see COLOR_VALUE<br>
Reserved7[2]		reserved, must be 0<br>
<br>
A FRAMESETLENGTH structure will follow depending on the value found in either RowQty or ColQty.  There could be multiple FRAMESETLENGTH structures defining the RowQty and ColQty values.</ul>



**See Also :**
[CDFRAME](/domino-c-api-docs/reference/Data/CDFRAME)
[CDFRAMESETHEADER](/domino-c-api-docs/reference/Data/CDFRAMESETHEADER)
[COLOR_VALUE](/domino-c-api-docs/reference/Data/COLOR_VALUE)
[fFSxxx](/domino-c-api-docs/reference/Symb/fFSxxx)
[FRAMESETLENGTH](/domino-c-api-docs/reference/Data/FRAMESETLENGTH)
---
