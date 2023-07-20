##### Symbolic Value : Views
##### NAVIGATE_xxx - How NIFReadEntries steps through a collection.
---
```
#include <nif.h>
```

**Symbolic Values :**

	NAVIGATE_CURRENT	  -  Remain at current position (reset position & return data).

	NAVIGATE_PARENT	  -  Up 1 level.

	NAVIGATE_CHILD	  -  Down 1 level to first child.

	NAVIGATE_FIRST_PEER	  -  First node at our level.

	NAVIGATE_LAST_PEER	  -  Last node at our level.

	NAVIGATE_CURRENT_MAIN	  -  Highest level non-category entry.

	NAVIGATE_ALL_DESCENDANTS	  -  NEXT, but only descendants below NIFReadEntries() - StartPos.

	NAVIGATE_CURRENT_HIT	  -  Remain at current position in hit's relevance rank array (in the order of the hit's relevance ranking).

	NAVIGATE_MASK	  -  Navigator code mask.

	NAVIGATE_MINLEVEL	  -  Honor "Minlevel" field in position. This flag which can be used with any other navigate flag. It causes the navigation to be limited to entries at a specific level (specified by the field "MinLevel" in the collection position) or any higher levels but never a level lower than the "MinLevel" level. Note that level 0 means the top level of the index, so the term "minimum level" really means the "topmost level" the navigation can move to. This can be used to find all entries below a specific position in the index, limiting yourself only to that subindex, and yet be able to use any of the navigators to move around within that subindex. If this flag is not specified, it defaults to level 0, meaning that all levels up to and including the topmost level in the collection will be included in the navigation.

	NAVIGATE_MAXLEVEL	  -  Honor "Maxlevel" field in position. This flag which can be used with any other navigate flag. It causes the navigation to be limited to entries at a specific level (specified by the field "MaxLevel" in the collection position) or any lower levels but never a level higher than the "MaxLevel" level. In other words, the MaxLevel field specifies the "bottommost level" that the navigation can move to. If this flag is not specified, it defaults to (MAXTUMBLERLEVELS -1), meaning that all levels down to and including the bottommost level in the collection will be included in the navigation.

	NAVIGATE_CONTINUE	  -  This flag can be combined with any navigation directive to prevent having a navigation (Skip) failure abort the (ReadEntries) operation. For example, this is used by the Notes user interface when getting the entries to display in the view, so that if an attempt is made to skip past either end of the index (e.g. using PageUp/PageDown), the skip will be left at the end of the index, and the return will return whatever can be returned using the separate return navigator.

This flag is also used to get the "last" N entries of a view by setting the Skip Navigator to NAVIGATE_NEXT | NAVIGATE_CONTINUE, setting the SkipCount to MAXDWORD, setting the ReturnNavigator to NAVIGATE_PREV_EXPANDED, and setting the ReturnCount to N (N must be greater than 0).


**Description :**

These flags control how NIFReadEntries steps through a collection. The flags are used to control both the order in which NIFReadEntries skips notes in a collection before reading any notes, and navigates the collection while it is being read.<br>

<ul>The minlevel and/or maxlevel navigation criteria will be used if the NAVIGATE_MINLEVEL and/or NAVIGATE_MAXLEVEL navigation flags are set in <b>either </b>the SkipNavigator or ReturnNavigator parameters to NIFReadEntries.  Regardless of which parameter these flags are set in, if the flags are set in either one of these parameters the flags will affect the collection levels that are used in <b>both</b> skip navigation and return navigation of the collection.</ul>



**See Also :**
[NIFReadEntries](/domino-c-api-docs/reference/Func/NIFReadEntries)
---
