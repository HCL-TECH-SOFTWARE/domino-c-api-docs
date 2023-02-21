##### Data Type : Rich Text
##### COLOR_VALUE - Components defining Color.
---
```
#include <colorods.h>
```
**Description :**

This data structure defines the three components of an RGB color which consist 
of a red, green, and blue color value.

Flags  set this member to: COLOR_VALUE_FLAGS_xxx
Component1 Red component value of RGB color.
Component2 Green component value of RGB color.
Component3 Blue component value of RGB color.

Example of colors and RGB values: 

BLACK  Component1 = 0 Component2 = 0 Component3 = 0
WHITE  Component1 = 255 Component2 = 255 Component3 = 255
GRAY  Component1 = 128 Component2 = 128 Component3 = 128
LT. GREEN  Component1 = 127 Component2 = 255 Component3 = 127
GREEN  Component1 = 63 Component2 = 128 Component3 = 63
LT. YELLOW Component1 = 128 Component2 = 128 Component3 = 63
YELLOW  Component1 = 255 Component2 = 255 Component3 = 127
CYAN  Component1 = 127 Component2 = 255 Component3 = 255
LT. CYAN  Component1 = 63 Component2 = 128 Component3 = 128
RED  Component1 = 255 Component2 = 0 Component3 = 0
GREEN  Component1 = 0 Component2 = 255 Component3 = 0
BLUE  Component1 = 0 Component2 = 0 Component3 = 255
MAGENTA  Component1 = 255 Component2 = 0 Component3 = 255
YELLOW  Component1 = 255 Component2 = 255 Component3 = 0
CYAN  Component1 = 0 Component2 = 255 Component3 = 255
DK. RED  Component1 = 128 Component2 = 0 Component3 = 0
DK. GREEN Component1 = 0 Component2 = 128 Component3 = 0
DK. BLUE  Component1 = 0 Component2 = 0 Component3 = 128
DK. MAGENTA Component1 = 128 Component2 = 0 Component3 = 128
DK. YELLOW Component1 = 128 Component2 = 128 Component3 = 0
DK. CYAN  Component1 = 0 Component2 =128 Component3 = 128

**See Also :**
[COLOR_VALUE_FLAGS_xxx](/domino-c-api-docs/reference/Symb/COLOR_VALUE_FLAGS_xxx)
---
