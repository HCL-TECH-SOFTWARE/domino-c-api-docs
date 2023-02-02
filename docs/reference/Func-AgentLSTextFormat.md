##### Function : Agents
##### AgentLSTextFormat - Convert LotusScript to IDE readable format.
---
##### #include <agents.h>
STATUS LNPUBLIC **AgentLSTextFormat(**

	DHANDLE  hSrc,
	DHANDLE *hDest,
	DHANDLE *hErrs,
	DWORD  dwFlags,
	DHANDLE *phData);
**Description :**
This function formats a raw block of LotusScript source code by rearranging the 
Declarations and the Options into the appropriate sections, and adding header 
comments that the Notes IDE uses for rendering the script.  This function 
supports LotusScript in the Script Libraries, Agents, Forms, Pages, Subforms, 
Views, Actions, Fields or Database Scripts.

**Parameters :**
Input :
hSrc  -  A handle to a  block of memory containing  LotusScript source code that is maintained in an Agent or a Script Library.  

Before calling this function, the program should use OSMemAlloc and OSLock to allocate a block of memory large enough to accomodate the LotusScript source text plus the null terminator.
Then, copy the LotusScript source code to this block of memory, and use OSUnlock to unlock the handle.

phData  -  Pointer to a handle. It should be set to the pointer of NULL ( If the LotusScript to be formatted is contained in an Agent, or the Script Library), or the structure SCRIPTCONTEXTDESCR (if the LotusScript to be formatted is contained in a Form, Page, Subform, View, Action, Field or Database Script).  Please see SCRIPTCONTEXTDESCR for more information.

Output :
(routine)  -   Return status of the call - indicates either success or what the error is.  The return error codes include:

NOERROR               - Success

ERR_MEMORY      - Could not allocate new Document for processing of data. 



hDest  -  A Pointer to a Handle.  The function will allocate a block of memory and put the Formatted LotusScript into this block of memory.  It is the caller's responsibility to free this block of memory using OSMemFree.  


hErrs  -  A Pointer to a Handle.  If errors occur during the Parsing/Analysis of the text, the function will allocate a block of memory and return the text and error numbers in this block of memory.  It is the caller's responsibility to free this block of memory using OSMemFree.   Errors reported are simple syntax errors such as If statements without a then, unterminated strings or Identifier names being too long.


dwFlags  -  Reserved for future expansion.  Should be set to ZERO; otherwise, unexpected results may occur in future releases.

**Sample Usage :**
```
 /*** Be sure to allocate enough memory for the script and the 
       null terminator.  */
    if (error = OSMemAlloc(0,strlen(szScript)+1,&hSource))
    {
       printf("Error: unable to alloc hSource.\n");
       goto Exit1;
    }
    sourceAllocated=1;

    /*** Copy the raw Lotus Script into the newly allocated memory 
    space. */
    pFormattedLS=OSLock(char,hSource);
    strcpy(pFormattedLS,szScript);
    OSUnlock(hSource);

    /*** Convert the raw Lotus Script to IDE conformed format.  */
    error = AgentLSTextFormat(hSource,&hDest, &hErrorBuffer,0,&hUnused);

    /*** Free hSource handle, and update memory allocation flags for
    hSource, hDest and hErrorBuffer handles. */
    OSMemFree(hSource);
    sourceAllocated=0;
    destAllocated=1;
    errorBufferAllocated=1;   

    if (error )
    { 
       printf("Error: Error in AgentLSTextFormat.\n");
       goto Exit1;
    }

    /*** If any script error, retrieve the error text from hErrorBuffer 
    handle; otherwise, retrieve the IDE conformed script.  */
    if (hErrorBuffer)
    {
       pFormattedLS=OSLock(char,hErrorBuffer);
       printf("\nError from AgentLSTextFormat: %s\n",pFormattedLS);
       OSUnlock(hErrorBuffer);
       error=1;
       goto Exit1;
    }
    else if (hDest)
    {
       OSMemFree(hErrorBuffer);
       errorBufferAllocated=0;
       pFormattedLS=OSLock(char,hDest);

       /*** When saving the formatted LS in the "$AssistAction" item, 
       the script should be ended with a null terminator, therefore, 
       we'll add one to the strlen(pFormattedLS) and save it in the 
       FormattedLSLen variable.  */

       FormattedLSLen=strlen(pFormattedLS)+1;
    }

.
.
.
    OSUnlock(hDest);
    OSMemFree(hDest);
    destAllocated=0;
.
.
.
Exit1:
    if (sourceAllocated)
       OSMemFree(hSource);

    if (destAllocated)
       OSMemFree(hDest);

    if (errorBufferAllocated)
       OSMemFree(hErrorBuffer);
 
```
**See Also :**
[OSLock](D:/md_files/OSLock.md)
[OSMemAlloc](D:/md_files/OSMemAlloc.md)
[OSMemFree](D:/md_files/OSMemFree.md)
[SCRIPTCONTEXTDESCR](D:/md_files/SCRIPTCONTEXTDESCR.md)
---
