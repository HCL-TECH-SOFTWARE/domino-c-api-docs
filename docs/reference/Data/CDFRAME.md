##### Data Type : Composite Data
##### CDFRAME - Used to specify an HTML FRAME element
---
```
#include <fsods.h>
```

**Definition :**
```
typedef struct{
	WSIG Header;
	DWORD Flags; /* fFRxxx unused bits must be set to 0 */

/* In 6 this word is used to signify variable data follows the frame */
/* the data is in the order of the bits, i.e. 0x8000 is the first chunk of   
   data*/
/* the first word of each set of data is the size then the data*/
	WORD  DataFlags;     
	BYTE  BorderEnable;  /* Specifies the FRAMEBORDER attribute for 
                                    this Frame element */
	BYTE  NoResize;   /* Specifies the NORESIZE attribute for this 
                                    Frame element */
	WORD  ScrollBarStyle;  /* Specifies the SCROLLING attribute for this
	                               * frame element.  Must be 
ALWAYS_ScrollStyle,
	      * NEVER_ScrollStyle or AUTO_ScrollStyle */
	WORD  MarginWidth;  /* Specifies the MARGINWIDTH attribute for 
                                    this frame element */
	WORD  MarginHeight;  /* Specifies the MARGINHEIGHT attribute for 
                                    this frame element */
	DWORD dwReserved;   /* Reserved for future use, must be 0 */
	WORD  FrameNameLength;  /* Length of FrameName string that follows. 
	                               * Set to 0 if not specified. */
	WORD Reserved1;
	WORD  FrameTargetLength;     /* Length of default target frame name. 
	        Set to 0 if not specified */
	COLOR_VALUE FrameBorderColor; /* Specifies the BORDERCOLOR attribute 
	        for this frame element */
	WORD wReserved;   /* Reserved for future use, must be 0 */
	/* Variable length data follows (strings not null terminated)
	 *  - Frame Name string (Specifies the NAME attribute for this frame 
element */
	/*  - Frame Target string */

	/*This is where the data assoiciated with the Dataflags word above 
begins*/

} CDFRAME;
```

**Description :**

Header
<ul><br>
Flags			see fFRxxx<br>
DataFlags			see fFRNotesxxx<br>
BorderEnable		Frame Border Attribute specified.<br>
NoResize			Specifies the NoReSize attribute to this Frame.<br>
ScrollBarStyle		see xxx_ScrollStyle<br>
MarginWidth		Margin Width of this Frame in pixels.<br>
MarginHeight		Margin Height of this Frame in pixels.<br>
dwReserved		Reserved, must be 0.<br>
FrameNameLength		Length of the frame name string.<br>
Reserved1			Reserved, must be 0.<br>
FrameTargetLength		Length of the default target frame name.<br>
FrameBorderColor		Specifies the Border Color.<br>
wReserved			Reserved, must be 0.<br>
<br>
Frame Name String and Target Name string follow the fixed portion of this CD Record.  The strings are not null terminated.<br>
<br>
</ul>



**See Also :**
[CDFRAMESETHEADER](/domino-c-api-docs/reference/Data/CDFRAMESETHEADER)
[COLOR_VALUE](/domino-c-api-docs/reference/Data/COLOR_VALUE)
[fFRNotesxxx](/domino-c-api-docs/reference/Symb/fFRNotesxxx)
[fFRxxx](/domino-c-api-docs/reference/Symb/fFRxxx)
[xxx_ScrollStyle](/domino-c-api-docs/reference/Symb/xxx_ScrollStyle)
---
