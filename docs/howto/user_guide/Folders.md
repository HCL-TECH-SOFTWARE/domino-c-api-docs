##### Chapter 6-6
##### Folders

<b><font size="5" color="#000080">Accessing Documents in Folders</font></b><br>
<br>
Folders are very similar to views. The HCL C API for Domino and Notes lets you access documents in a folder just as you access documents in a view.<br>
 <br>
You can create and access private and shared database folders. However, you cannot create folders that are &quot;Personal on first use,&quot; nor can you create private folders that are stored in the desktop file. In the Notes user interface, newly created private folders are generally stored in a specified database. However, if the user does not have database access rights for the creation of private folders, the folder is created in the user's desktop file. In a C API program, you cannot create a folder if the user does not have database access rights for the creation of private folders. Also, a C API program cannot access private folders that are stored in the desktop file.<br>
<br>
To access a private folder that is stored in the database, use NIFFindPrivateDesignNote and set the class parameter to NOTE_CLASS_VIEW. To access a shared folder, use NIFFindView. Then use NIFOpenCollection and NIFReadEntries to obtain the documents in the folder just as you would for a view.<br>
<br>
<b><font size="5" color="#000080">Creating and Manipulating Folders</font></b><br>
<br>
The C API provides functions that let you create, copy, remove, move, and rename folders. You can also add documents to folders and remove documents from folders. For details, see the Folder functions in the <i>Reference.</i>
---
