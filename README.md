# Plugin for SourceMod developers
## About

Here the new API docs with all (I hope) function, define, enum, methodmap and fixed xml structure. Docs were generated by reworked generator plugin.

## Plugin features:
 - Generate auto-completion files
 - Generate inline docs (*sourcemod.xml*)
 - Supports SourceMod 1.7 API specifics
 
## New in v1.2:
 - Added xml filter
 - Added more console stats
 - Better way to detect commentary lines
 - Code optimization
 - Detect methodmap
 - Detect enum & define correctly
 - Detect all func params

## Server command:
**sm_makedocs** - starts to parse SourceMod includes and generates output files

## Methodmap notes:
![Docs screenshot](https://github.com/raziEiL/SourceMod-Npp-Docs/blob/master/img/img.png "Inline docs: methodmap strings")  
These strings are not exist SourceMod function! Purpose of these strings provide access to docs and show methodmap structure. Notepad++ don't reacts on dots in names (exp: LineNumber.get) and docs not shown, so I replaced `.` with `_` symbol
>If you want to use string as code you must remove prefix and separate `_` with `.`  
>If you want to watch docs you must do the vice versa 

### Prefix structure:

| Type | With tag | Without tag |
|------| ------ | ------ |
| Constructor | METHODMAP_`%1`_`%2`\_CONSTRUCTOR_`%3` | METHODMAP_`%1`\_CONSTRUCTOR_`%3` |
| Method | METHODMAP_`%1`_`%2`_METHOD\_`%3` | METHODMAP_`%1`\_METHOD_`%3` |
| Property | METHODMAP_`%1`_`%2`_PROP\_`%3` | METHODMAP_`%1`_PROP\_`%3` |

Where: `%1` - Class name, `%2` - Tag name, `%3` - Real method/property/constructor name

**PREFIX** - Text before `%3` param (e.g., `METHODMAP_ConVar_PROP_`Flags)

### Examples:

**String to watch docs:**  
Method: Clone
Prefix: METHODMAP_ArrayList_Handle_METHOD_  
Result: METHODMAP_ArrayList_Handle_METHOD_Clone

**String to use as code:**  
Docs string: METHODMAP_ArrayStack_PROP_BlockSize_get  
Removes prefix: METHODMAP_ArrayStack_PROP_
Result: my_code.BlockSize.get()
