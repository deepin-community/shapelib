dbfcreate(1) -- Create an empty xBase DBF file
==============================================

##SYNOPSIS
`dbfcreate` _xbase_file_ [[`-s` _field_name_ _width_] | [`-n` _field_name_ _width_ _decimals_],...]

##DESCRIPTION
Creates an empty DBF file called _xbase_file_ with columns described by all the `-s` and `-n` options that follow.

##OPTIONS
 * _xbase_file_:
 the name of xBase file to be created. Doesn't need the extension.
 * `-s` _field_name_ _width_:
 creates a string field with name _field_name_ and size _width_.
 * `-n` _field_name_ _width_ _decimals_:
 creates a numeric field with name _field_name_, width of _width_ and with _decimals_ places sized by decimals.

##EXAMPLE
`dbfcreate` _testbase_ `-s` `NAME` _20_, `-n` `AREA` _9_ _3_, `-n` `VALUE` _9_ _2_

this will create a file named _testbase_`.dbf` with 3 fields: `NAME` (string (_20_)), `AREA` (float (_9_,_3_)) and `VALUE` (float (_9_,_2_))

##EXIT STATUS
 * `0`:
 Successful program execution.
 * `1`:
 Missing _xbase_file_ argument.
 * `2`:
 Failed to create the file _xbase_file_ for writing.
 * `3`:
 Missing _field_name_, _width_, or _decimals_ argument for a `-s` or `-n` option.
 * `4`:
 Failed to add a column given by a `-s` or `-n` option.

##DIAGNOSTICS
The following diagnostics may be issued on stdout:

DBFCreate(_xbase_file_) failed.

DBFAddField(_field_name_,FTString,_width_,0) failed.

DBFAddField(_field_name_,FTDouble,_width_,_decimals_) failed.

Argument incomplete, or unrecognised: _arg_

##AUTHOR
`dbfcreate` is part of shapelib, maintained by Frank Warmerdam. This guide was created by Eduardo Patoo Kanegae and converted to manpage by Johan Van de Wauw. It was further enhanced with the man page written by Joonas Pihlaja (jpihlaja@cc.helsinki.fi).

##SEE ALSO
`dbfadd`(1), `dbfcat`(1), `dbfdump`(1), `dbfinfo`(1), `shpadd`(1), `shpcat`(1), `shpcentrd`(1), `shpcreate`(1), `shpdump`(1), `shpdxf`(1), `shpfix`(1), `shpinfo`(1), `shpproj`(1), `shprewind`(1), `shptest`(1)

