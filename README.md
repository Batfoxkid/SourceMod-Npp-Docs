Sourcemod Pawn language docs for Notepad++

Sad but sourcemod.xml docs outdated. Finally i did it. Here the new API docs (sm 1.9.0) with all (I hope) function, define, enum, methodmap and fixed xml structure. Docs were generated by reworked generator plugin.


Plugin feature:
generate auto-completion/inline docs files

New in v1.2:
added xml filter
added more console stats
better way to detect commentary lines
code optimization
detect methodmap
detect enum & define correctly
detect all func params

Server command:
sm_makedocs

Methodmap notes:
Notepad++ don't react on dots in names (LineNumber.get) and docs not shown, so I replace '.' with '_' symbol


This strings are not SourceMod function! Purpose of this strings provide access to docs and show methodmap structure.
If you want to use it as code you must remove prefix and separate '_' with '.'
If you want to watch docs you must do the vice versa 

Prefix structure:

PREFIX - All text before Method/Property/Constructor name

I. With Tag
METHODMAP_%1_%2_METHOD_%3
METHODMAP_%1_%2_PROP_%3

II. Without Tag
METHODMAP_%1_METHOD_%3
METHODMAP_%1_PROP_%3

Where:
%1 - Class name
%2 - Tag name
%3 - Method/Property/Constructor name

Example to watch docs: 
Method: Clone
Prefix: METHODMAP_ArrayList_Handle_METHOD_
Result: METHODMAP_ArrayList_Handle_METHOD_Clone

Example to use as code:
Docs: METHODMAP_ArrayStack_PROP_BlockSize_get
Result: my_code.BlockSize.get()