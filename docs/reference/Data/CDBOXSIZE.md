##### Data Type : Composite Data
##### CDBOXSIZE - Defines size information for a layer box. 
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct
 {
 BSIG Header;
 LENGTH_VALUE Width;
 LENGTH_VALUE Height;
 LENGTH_VALUE Reserved[4]; /* reserved for future use */
 DWORD dwReserved[4]; /* reserved for future use */
 } CDBOXSIZE;
```

**Description :**

This CD record contains size information for a layer box. The units (pixels, twips, etc.) for the Width and Height are set in the &quot;Units&quot; members of the &quot;Top&quot;, &quot;Left&quot;, &quot;Bottom&quot; and &quot;Right&quot; members of the CDPOSITIONING structure. The fields in this record are:
<ul><br>

<ul>Header		Signature and Length of this CD record.<br>
Width		The width of the box. <b>  </b><br>
Height		The height of the box. <b>  </b><br>
Reserved	Reserved for future use. <b> </b><br>
dwReserved	Reserved for future use.</ul>
</ul>



**See Also :**
[CDLAYER](/domino-c-api-docs/reference/Data/CDLAYER)
[CDPOSITIONING](/domino-c-api-docs/reference/Data/CDPOSITIONING)
---
