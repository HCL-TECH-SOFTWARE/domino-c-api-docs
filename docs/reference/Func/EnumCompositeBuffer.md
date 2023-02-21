##### Function : Composite Data
##### EnumCompositeBuffer - Call action routine for each Composite Data record in a buffer.
---
```
#include <ods.h>
STATUS LNPUBLIC EnumCompositeBuffer(

	BLOCKID  ItemValue,
	DWORD  ItemValueLength,
	ActionRoutinePtr  ActionRoutine,
	void far *vContext);
```
**Description :**

This function parses the value block of an item of type TYPE_COMPOSITE in a 
buffer. For each CD record in this item, it calls an action routine specified 
by the user.  Since each CD record may have a different header and a different 
length, parsing a CD buffer is fairly complex. Therefore, this function is the 
recommended way to access the CD records that constitute a TYPE_COMPOSITE item.

This function takes, as input, the BLOCKID of the value of a TYPE_COMPOSITE 
item, its length in a DWORD, the address of an Action Routine (the Action 
Routine is supplied by the user), and the address of any data (for context) 
that is to be passed to the Action Routine.  It then calls the Action Routine 
once for each CD record in the item, until the entire item is processed.

**Parameters :**
Input :
ItemValue  -  BLOCKID associated with value of TYPE_COMPOSITE item

ItemValueLength  -  DWORD length of TYPE_COMPOSITE item

ActionRoutine  -  A pointer to an Action Routine.  The following is a template for the action routine specification:   

ActionRoutine(char far *RecordPtr, WORD RecordType, DWORD RecordLength, void far *vContext);

EnumCompositeBuffer calls the Action Routine with arguments describing each Composite Data record in the TYPE_COMPOSITE (Rich Text) item.

The first argument is a (char far *) pointer to the current Composite Data record. The second is a SIG_CD_xxx signature WORD. The third argument is the DWORD length of the object pointed to by the first argument.  The fourth argument is a pointer to user data.  It is supplied as input to EnumCompositeBuffer (fourth argument).  This provides a way to pass context data to the Action Routine.

vContext  -  A pointer to user data.  This pointer is then passed to the Action Routine.  It provides a way to pass non-global data to the Action Routine.

Output :
(routine)  -  Return indicates either success or what the error is. The return codes include: 

NOERROR - Composite Data successfully enumerated.
ERR_ODS_ENUM_COMPLETE - upon successful enumeration of all Composite Data (CD) records in the buffer
ERR_DATATYPE - if buffer does not contain an item of TYPE_COMPOSITE
ERR_xxx - STATUS returned from a lower-level Domino function called in the action routine and passed back.



**Sample Usage :**
```
#include <ods.h>

{
/*
 * typedef of a pointer pointer to the action routine is in ods.h
 *
 *
 * typedef STATUS (LNCALLBACKPTR ActionRoutinePtr)(char far *,
 *                                              WORD,
 *                                              DWORD,
 *                                              void far *);
 */

   ActionRoutinePtr Action;  /* Pointer to action routine for
                                EnumCompositeBuffer. */

/*
 * Get pointer to the action routine to be invoked by
 * EnumCompositeBuffer.
 */

   Action = (ActionRoutinePtr) MakeProcInstance(FormFields, hInst);
    
/*
 * For each CD record found in the Body of the Form note,
 * EnumCompositeBuffer will invoke the action routine FormFields.
 */

   sError = EnumCompositeBuffer(ValueBlockID,
                                  dwLength,
                                  Action,
                                  pOutputBuffer);
}
```
**See Also :**
[ConvertItemToCompositeExt](/domino-c-api-docs/reference/Func/ConvertItemToCompositeExt)
[NSFItemConvertToText](/domino-c-api-docs/reference/Func/NSFItemConvertToText)
[NSFItemConvertValueToText](/domino-c-api-docs/reference/Func/NSFItemConvertValueToText)
[NSFItemInfo](/domino-c-api-docs/reference/Func/NSFItemInfo)
[NSFNoteClose](/domino-c-api-docs/reference/Func/NSFNoteClose)
[NSFNoteOpen](/domino-c-api-docs/reference/Func/NSFNoteOpen)
---
