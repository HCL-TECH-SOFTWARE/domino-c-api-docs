##### Data Type : Composite Data
##### CDLAYER - Start record for a layer on a form.
---
```
#include <editods.h>
```

**Definition :**

typedef struct
 {
 BSIG Header;
 DWORD Reserved[4];
 } CDLAYER;

**Description :**

The definition for a layer on a form is stored as CD records in the $Body item of the form note.  A layer is comprised of a Layer Object Run (pointer to box that represents the layer), Box Run and Position Data. <br>

<ul>An example of the ODS stream describing a layer and its contents:<br>
CDBEGIN - (signature CDLAYER)<br>
CDLAYER<br>
CDPOSITIONING<br>
CDBOXSIZE<br>
CDBEGIN (signature CDBACKGROUNDPROPERTIES) - optional<br>
CDBACKGROUNDPROPERTIES - optional<br>
CDRESOURCE (SIG_CD_HREF of shared image) - optional<br>
CDCOLOR (SIG_CD_BACKGROUNDCOLOR) - optional, if not present the background is transparent<br>
CDEND (signature CDBACKGROUNDPROPERTIES) - optional<br>
Next follow the cd records of the paragraphs in the layer.<br>
If another CDBEGIN record for a layer is encountered before the CDEND of the previous layer, this means this is the start of a child layer.<br>
CDEND - (of signature SIG_CD_LAYER)<br>
<br>
You can design a form to have text, images, and all other document content positioned anywhere above or below the normal content layer.   With layers you can position text over an image. <br>
<br>
A layer is like a table cell that you can position anywhere. A layer behaves like a table cell in that it is a container to put other objects in.  Unlike a table cell, a layer has handles for moving and sizing it. A z-index on a layer controls its position in relation to other layers (in front of or behind them).</ul>



**See Also :**
[CDBACKGROUNDPROPERTIES](/domino-c-api-docs/reference/Data/CDBACKGROUNDPROPERTIES)
[CDBOXSIZE](/domino-c-api-docs/reference/Data/CDBOXSIZE)
[CDLAYER_VERSIONxxx](/domino-c-api-docs/reference/Symb/CDLAYER_VERSIONxxx)
[CDPOSITIONING](/domino-c-api-docs/reference/Data/CDPOSITIONING)
---
