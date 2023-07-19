##### Data Type : Composite Data
##### CDLINKCOLORS - HTML Link Colors
---
```
#include <colorods.h>
```

**Definition :**

typedef struct {
   WSIG        Header;         /* Signature and len of this rec */
   DWORD       dwFlags;
   COLOR_VALUE unvisitedColor; /* Color of unvisited links */
   COLOR_VALUE activeColor;    /* Color of active link */
   COLOR_VALUE visitedColor;   /* Color of visited links */
   DWORD       dwSpares[4];
} CDLINKCOLORS;

**Description :**

Color properties to various HTML Links.
<ul><br>
<br>
Header		Signature and length of this record<br>
dwFlags		Not Used<br>
unvisitedColor	Color of unvisited links<br>
activeColor		Color of active links<br>
visitedColor		Color of visited links<br>
dwSpares		Not Used</ul>



**See Also :**
---
