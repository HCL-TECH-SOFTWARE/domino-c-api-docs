##### Data Type : Composite Data
##### CDLAYER - Start record for a layer on a form.
---
```
#include <editods.h>
```
**Description :**

The definition for a layer on a form is stored as CD records in the $Body item 
of the form note.  A layer is comprised of a Layer Object Run (pointer to box 
that represents the layer), Box Run and Position Data. 

An example of the ODS stream describing a layer and its contents:
CDBEGIN - (signature CDLAYER)
CDLAYER
CDPOSITIONING
CDBOXSIZE
CDBEGIN (signature CDBACKGROUNDPROPERTIES) - optional
CDBACKGROUNDPROPERTIES - optional
CDRESOURCE (SIG_CD_HREF of shared image) - optional
CDCOLOR (SIG_CD_BACKGROUNDCOLOR) - optional, if not present the background is 
transparent
CDEND (signature CDBACKGROUNDPROPERTIES) - optional
Next follow the cd records of the paragraphs in the layer.
If another CDBEGIN record for a layer is encountered before the CDEND of the 
previous layer, this means this is the start of a child layer.
CDEND - (of signature SIG_CD_LAYER)

You can design a form to have text, images, and all other document content 
positioned anywhere above or below the normal content layer.   With layers you 
can position text over an image. 

A layer is like a table cell that you can position anywhere. A layer behaves 
like a table cell in that it is a container to put other objects in.  Unlike a 
table cell, a layer has handles for moving and sizing it. A z-index on a layer 
controls its position in relation to other layers (in front of or behind them).


**See Also :**
[CDBACKGROUNDPROPERTIES](/reference/Data/CDBACKGROUNDPROPERTIES)
[CDBOXSIZE](/reference/Data/CDBOXSIZE)
[CDLAYER_VERSIONxxx](/reference/Symb/CDLAYER_VERSIONxxx)
[CDPOSITIONING](/reference/Data/CDPOSITIONING)
---
