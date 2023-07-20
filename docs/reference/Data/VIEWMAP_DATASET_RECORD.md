##### Data Type : Navigators
##### VIEWMAP_DATASET_RECORD - Navigator settings CD record.
---
```
#include <vmods.h>
```

**Definition :**
```
typedef struct {
   WSIG  Header;
   WORD  Version;
 WORD  ViewNameLen; /* length of initial view name; 0 if none */
   WORD  Gridsize;    /* (in pixels) */
   WORD  Flags;       /* VM_DSET_xxx */
   WORD  bAutoAdjust;
   WORD  BGColor;
   WORD  SeqNums[VM_MAX_OBJTYPES]; /* highest sequence number for */
                                  /* each type of draw object */
                                  /* supported (w/extra space for */
                                  /* future) */
   VIEWMAP_STYLE_DEFAULTS StyleDefaults;
   WORD  NumPaletteEntries;
   WORD  ViewDesignType;           /* design type of initial view */
   COLOR_VALUE BGColorValue;       /* BG color stored in some color
                                      space */
   DWORD spare[14];
} VIEWMAP_DATASET_RECORD;
```

**Description :**

The VIEWMAP_DATASET_RECORD stores the settings and defaults for a Navigator.  The fields in this structure are:
<ul><br>
<br>
<tt><font size="2">Header &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Defines this composite data item as a</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; VIEWMAP_DATASET_RECORD item.</font></tt><br>
<tt><font size="2">Version &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Version number of this structure.</font></tt><br>
<tt><font size="2">ViewNameLen &nbsp; &nbsp; &nbsp; Length of the inital view name; &nbsp;may be 0.</font></tt><br>
<tt><font size="2">Gridsize &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Size of any displayed grid, in pixels.</font></tt><br>
<tt><font size="2">Flags &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Option flags (see VM_DSET_xxx).</font></tt><br>
<tt><font size="2">bAutoAdjust &nbsp; &nbsp; &nbsp; If TRUE, automatically adjust the display to</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; show as much of the Navigator as possible.</font></tt><br>
<tt><font size="2">BGColor &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Background color for the Navigator.</font></tt><br>
<tt><font size="2">SeqNums &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Each type of graphical object is numbered in</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; sequence. &nbsp;This array stores the highest number</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; assigned in this navigator.</font></tt><br>
<tt><font size="2">StyleDefaults &nbsp; &nbsp; Structure containing the default settings for</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; graphical elements.</font></tt><br>
<tt><font size="2">NumPaletteEntries Number of color palette entries required to</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; display this Navigator.</font></tt><br>
<tt><font size="2">ViewDesignType &nbsp; &nbsp;Design type of the initial view.</font></tt><br>
<tt><font size="2">BGColorValue</font></tt><br>
<tt><font size="2">spare &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Reserved; must be 0.</font></tt></ul>



**See Also :**
[VM_MAX_OBJTYPES](/domino-c-api-docs/reference/Symb/VM_MAX_OBJTYPES)
[VIEWMAP_STYLE_DEFAULTS](/domino-c-api-docs/reference/Data/VIEWMAP_STYLE_DEFAULTS)
[VIEWMAP_VERSION](/domino-c-api-docs/reference/Symb/VIEWMAP_VERSION)
[VM_DSET_xxx](/domino-c-api-docs/reference/Symb/VM_DSET_xxx)
---
