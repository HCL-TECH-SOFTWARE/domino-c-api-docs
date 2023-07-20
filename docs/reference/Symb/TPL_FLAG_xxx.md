##### Symbolic Value : Rich Text
##### TPL_FLAG_xxx - Flags defined for the FormFlags, FormFlags2 or FormFlags3 members of the CDDOCUMENT data structure.
---
```
#include <editods.h>
```

**Symbolic Values :**

	TPL_FLAG_REFERENCE	  -  FormFlags - Use Reference Note.

	TPL_FLAG_MAIL	  -  FormFlags - Documents should be mailed when they are saved.

	TPL_FLAG_NOTEREF	  -  FormFlags - Add note reference to "reference note".

	TPL_FLAG_NOTEREF_MAIN	  -  FormFlags - Add note reference to main parent of "reference note".

	TPL_FLAG_RECALC	  -  FormFlags - When leaving a field, recalculate its value.

	TPL_FLAG_BOILERPLATE	  -  FormFlags - Store the form used to compose the note within the note.

	TPL_FLAG_FGCOLOR	  -  FormFlags - Use the foreground color to paint.

	TPL_FLAG_SPARESOK	  -  FormFlags - Spare DWORDS have been zeroed.

	TPL_FLAG_ACTIVATE_OBJECT_COMP	  -  FormFlags - Activate OLE objects when composing a new note.

	TPL_FLAG_ACTIVATE_OBJECT_EDIT	  -  FormFlags - Activate OLE objects when editing an existing note.

	TPL_FLAG_ACTIVATE_OBJECT_READ	  -  FormFlags - Activate OLE objects when reading an existing note.

	TPL_FLAG_SHOW_WINDOW_COMPOSE	  -  FormFlags - Show editor window if the flag TPL_FLAG_ACTIVATE_OBJECT_COMP is set.

	TPL_FLAG_SHOW_WINDOW_EDIT	  -  FormFlags - Show editor window if the flag TPL_FLAG_ACTIVATE_OBJECT_EDIT is set.

	TPL_FLAG_SHOW_WINDOW_READ	  -  FormFlags - Show editor window if the flag TPL_FLAG_ACTIVATE_OBJECT_READ is set.

	TPL_FLAG_UPDATE_RESPONSE	  -  FormFlags - V3 Updates to this note become responses to it.

	TPL_FLAG_UPDATE_PARENT	  -  FormFlags - V3 Updates to this note become its parent.

	TPL_FLAG_INCLUDEREF	  -  FormFlags2 - insert copy of ref note

	TPL_FLAG_RENDERREF	  -  FormFlags2 - render ref (else it's a doclink)

	TPL_FLAG_RENDCOLLAPSE	  -  FormFlags2 - render it collapsed?

	TPL_FLAG_EDITONOPEN	  -  FormFlags2 - edit mode on open

	TPL_FLAG_OPENCNTXT	  -  FormFlags2 - open context panes

	TPL_FLAG_CNTXTPARENT	  -  FormFlags2 - context pane is parent

	TPL_FLAG_MANVCREATE	  -  FormFlags2 - manual versioning

	TPL_FLAG_UPDATE_SIBLING	  -  FormFlags2 - updates are sibblings

	TPL_FLAG_ANONYMOUS	  -  FormFlags2 - V4 Anonymous form

	TPL_FLAG_NAVIG_DOCLINK_IN_PLACE	  -  FormFlags2 - Doclink dive into same window

	TPL_FLAG_INTERNOTES	  -  FormFlags2 - InterNotes special form

	TPL_FLAG_DISABLE_FX	  -  FormFlags2 - Disable FX for this doc

	TPL_FLAG_NOMENUS	  -  FormFlags2 - Disable menus for this doc

	TPL_FLAG_CHECKDISPLAY	  -  FormFlags2 - Check display before displaying background

	TPL_FLAG_FORMISRTL	  -  FormFlags2 - This is a Right to Left form.

	TPL_FLAG_HIDEBKGRAPHIC	  -  FormFlags2 - Hide Background graphic in Design Mode.

	TPL_FLAG_RESIZEHEADER	  -  FormFlags3 - Editor resizes header area to contents.

	TPL_FLAG_NOINITIALFOCUS	  -  FormFlags3 - No initial focus to any object on a form or page.

	TPL_FLAG_SIGNWHENSAVED	  -  FormFlags3 - Sign this document when it gets saved.

	TPL_FLAG_NOFOCUSWHENF6	  -  FormFlags3 - No focus when doing F6 or tabbing.

	TPL_FLAG_RENDERPASSTHROUGH	  -  FormFlags3 - Render pass through HTML in the client.

	TPL_FLAG_NOADDFIELDNAMESTOINDEX	  -  FormFlags3 - Don't automatically add form fields to field index.

	TPL_FLAG_CANAUTOSAVE	  -  FormFlags3 - Autosave Documents created using this form.


**Description :**

These are the flags that may be specified in the FormFlags, FormFlags2 or FormFlags3 members of the CDDOCUMENT data structure. They are used to define document-wide attributes.


**See Also :**
[CDDOCUMENT](/domino-c-api-docs/reference/Data/CDDOCUMENT)
---
