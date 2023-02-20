##### Chapter 7-6
##### Finding the Components of a Rich Text Field

The C API function EnumCompositeBuffer scans a rich text field, finds each CD record in the field, and calls an action routine for each record. EnumCompositeBuffer finds CD records in a manner similar to the way NSFSearch finds documents. <br>
<br>
EnumCompositeBuffer is given a BLOCKID of the value of a TYPE_COMPOSITE field, the field's length in a DWORD, the address of an action routine (written by you), and the address of any data that you want to<font color="#FF0000"> </font>pass to the action routine. EnumCompositeBuffer then calls the action routine with each CD record until the entire field has been processed.<br>
<br>
EnumCompositeBuffer calls the action routine with arguments describing each CD record in the TYPE_COMPOSITE (rich text) item. The first argument is a (char far *) pointer to the current CD record. The second is a SIG_CD signature WORD. The third argument is the DWORD length of the object pointed to by the first argument. The fourth argument is a pointer to user data which is supplied as input to EnumCompositeBuffer (fourth argument). This lets you<font color="#FF0000"> </font>pass non-global data to your<font color="#FF0000"> </font>action routine.
---
