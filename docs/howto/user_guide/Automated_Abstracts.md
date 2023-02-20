##### Chapter 12-13
##### Automated Abstracts

The C API routine Abstract allows a C API program to use the automated abstract engine used by the @Abstract function. The automated abstract engine can select the important pieces of a message, based on a number of different criteria; abbreviate words to reduce the length of a piece of text; and remove unnecessary components of messages, such as mail headers or unneeded spaces.<font color="#FF0000">  </font>Please see the @Abstract documentation in the the <i>HCL Domino Designer Help</i> database for additional requisites, such as using abbreviation text files.  These requisites apply to both the @Abstract function and the Abstact C API.<br>
<br>
The Abstract routine is given the text to abstract, a maximum length for the abstract, and a set of commands that determine how to process the text.  Abstract can process only single-byte characters; multi-byte characters give unpredictable results.<br>
<br>
<br>
<b><font size="5" color="#000080">&quot;Chunks&quot;</font></b><br>
<br>
The text to be abstracted is treated as a series of &quot;chunks&quot; of text.  There are three types of chunks: text, mail headers, and punctuation.  Text chunks are basically sentences: character strings that end with a punctuation character.  The punctuation character is not included; it becomes a separate punctuation chunk.  Mail header chunks are identified by mail header keywords, followed by a colon, followed by a white<b><font color="#FF0000"> </font></b>space character (for example, &quot;Subject: &quot;, &quot;From: &quot;, or &quot;To: &quot;).<br>
<br>
<br>
<b><font size="5" color="#000080">Parameters</font></b><br>
<br>
A number of internal parameters control the processing and output format of Abstract.  You can set these parameters by including a parameter assignment in the command string.  Parameter assignments consist of a parameter keyword, an equals sign, and the parameter value.  Parameter names are not case-sensitive, but case is preserved in string parameter values.<br>
<br>
You can use &quot;false&quot;, &quot;no&quot;, or &quot;0&quot; to set Boolean parameters to False.  To set these parameters to True, use &quot;true&quot;, &quot;yes&quot;, or &quot;1&quot;, or simply include the parameter name with no value.  The Boolean parameters are:<br>

<ul>ab-usedict=
<ul>Use the abbreviations dictionary to identify abbreviations. The default is True.<br>
</ul>
ab-dropvowels=
<ul>Remove vowels from words when abbreviating the text. The default is False.<br>
</ul>
ab-dropfirstvowels=
<ul>Remove the first vowel from each word (even if it's the first letter) when abbreviating the text. The default is False.<br>
</ul>
ab-trimpunct=
<ul>Trim all white space from around punctuation when abbreviating the text. The default is False.<br>
</ul>
ab-trimwhite=
<ul>Trim white space to a single space when abbreviating the text. The default is True.</ul>
</ul>
<br>
You can set string parameters to any character string that does not include white space, although ChunkSep is a special case. The string parameters are:<br>

<ul>ChunkBegin=
<ul>This string will be written at the beginning of the output buffer. The default is &quot;&quot; (an empty string).<br>
</ul>
ChunkSep=
<ul>This string will be written at the end of each chunk, to delimit the chunks. The default is &quot; &quot; (a single space). Three special values are supported:
<ul>space - Use a single space<br>
lf - Use a linefeed character<br>
crlf - Use a carriage return/linefeed pair<br>
</ul>
</ul>
ChunkEnd=
<ul>This string will be written after all chunks have been output. The default is &quot;&quot; (an empty string).</ul>
</ul>
<br>
<br>
<b><font size="5" color="#000080">Commands</font></b><br>
<br>
You can pass any number of commands (along with parameter settings) to Abstract in the null-terminated string argument szKeywords. Commands and parameter settings are delimited by whitespace chacters. The supported commands are:<br>

<ul>textonly
<ul>Delete all mail header and punctuation chunks. Subsequent commands will have only text chunks on which to operate.<br>
</ul>
countwords
<ul>The words in the text are tallied and a &quot;significance&quot; value is computed for each word.</ul>
<br>
save
<ul>Save the current state of the abstraction engine on an internal stack, including the current state of the text. You can use the restore command to restore these saved states.</ul>
<br>
restore
<ul>Restore the most recently saved state of the abstraction engine. If no states have been stored, this command has no effect.</ul>
<br>
tryfit
<ul>Determine whether the abstract will fit into the output buffer space provided. If it fits, the current state of the document is written to the output buffer and Abstract returns. Any remaining commands are ignored.</ul>
<br>
abbrev
<ul>Apply the abbreviation rules to the text.</ul>
<br>
sortchunks
<ul>Sort the chunks according to a &quot;significance value.&quot; The significance of a chunk is a function of the number of words in the chunk, the significance values of the words in the chunk, and the type and position of the chunk.<br>
<br>
If you used the countwords command to compute word significance values, the significance values for the words are added and the total is used for the significance of the chunk.</ul>
<br>
nostoplist
<ul>Disable use of the &quot;stop list,&quot; which is a list of words that are normally insignificant, such as &quot;the,&quot; &quot;of,&quot; and &quot;and.&quot;</ul>
<br>
nosiglist
<ul>Disable use of the significant word list, which is a list of words that are normally significant, such as &quot;urgent&quot; &quot;important,&quot; or &quot;priority.&quot;</ul>
</ul>

---
