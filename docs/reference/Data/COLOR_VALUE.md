##### Data Type : Rich Text
##### COLOR_VALUE - Components defining Color.
---
```
#include <colorods.h>
```

**Definition :**

typedef struct {
 WORD Flags;
 BYTE Component1;
 BYTE Component2;
 BYTE Component3;
 BYTE Component4;

	/* RGB color space 
 * Component1 = red;
 * Component2 = green;
 * Component3 = blue;
 * Component4 = unused;
 */
} COLOR_VALUE;


**Description :**

This data structure defines the three components of an RGB color which consist of a red, green, and blue color value.
<ul><br>
<br>
Flags		set this member to: COLOR_VALUE_FLAGS_xxx<br>
Component1	Red component value of RGB color.<br>
Component2	Green component value of RGB color.<br>
Component3	Blue component value of RGB color.<br>
<br>
Example of colors and RGB values: <br>
<br>
BLACK		Component1 = 0	Component2 = 0	Component3 = 0<br>
WHITE		Component1 = 255	Component2 = 255	Component3 = 255<br>
GRAY		Component1 = 128	Component2 = 128	Component3 = 128<br>
LT. GREEN		Component1 = 127	Component2 = 255	Component3 = 127<br>
GREEN		Component1 = 63	Component2 = 128	Component3 = 63<br>
LT. YELLOW	Component1 = 128	Component2 = 128	Component3 = 63<br>
YELLOW		Component1 = 255	Component2 = 255	Component3 = 127<br>
CYAN		Component1 = 127	Component2 = 255	Component3 = 255<br>
LT. CYAN		Component1 = 63	Component2 = 128	Component3 = 128<br>
RED		Component1 = 255	Component2 = 0	Component3 = 0<br>
GREEN		Component1 = 0	Component2 = 255	Component3 = 0<br>
BLUE		Component1 = 0	Component2 = 0	Component3 = 255<br>
MAGENTA		Component1 = 255	Component2 = 0	Component3 = 255<br>
YELLOW		Component1 = 255	Component2 = 255	Component3 = 0<br>
CYAN		Component1 = 0	Component2 = 255	Component3 = 255<br>
DK. RED		Component1 = 128	Component2 = 0	Component3 = 0<br>
DK. GREEN	Component1 = 0	Component2 = 128	Component3 = 0<br>
DK. BLUE		Component1 = 0	Component2 = 0	Component3 = 128<br>
DK. MAGENTA	Component1 = 128	Component2 = 0	Component3 = 128<br>
DK. YELLOW	Component1 = 128	Component2 = 128	Component3 = 0<br>
DK. CYAN		Component1 = 0	Component2 =128	Component3 = 128</ul>



**See Also :**
[COLOR_VALUE_FLAGS_xxx](/domino-c-api-docs/reference/Symb/COLOR_VALUE_FLAGS_xxx)
---
