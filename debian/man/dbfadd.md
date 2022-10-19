dbfadd(1) -- add a row to an xBase DBF file
===========================================

##SYNOPSIS
`dbfadd` _xbase_file_ _field_values..._

##DESCRIPTION
Adds a row to the DBF file named by _xbase_file_ with column values given by the _field_values_ options that follow.  A NULL value is denoted by an empty argument.

##OPTIONS
 *  _xbase_file_:
 the name of an existing xBase file
 *  _field_values_:
 list of values to be inserted into the xBase file. You must specify a number of values equal to the number of fields the xBase file has. The order of values must also reflect the order of fields inside xBase file.

##EXAMPLE
`dbfadd` _testbase.dbf_ _REGION1_ _25.656_ _150.22_

 Assuming that _testbase.dbf_ has 3 fields (`NAME`, `AREA` and `VALUE`), this command line will insert a new record into _testbase.dbf_ with the value "_REGION1_" for `NAME`, '_25.656_' for `AREA` and '_150.22_' for `VALUE` field.

##EXIT STATUS
 * `0`:
 Successful program execution.
 * `1`:
 Missing _xbase_file_ or _field_values_ arguments.
 * `2`:
 Failed to open _xbase_file_ for reading and appending.
 * `3`:
 Too few values in _field_values..._

##DIAGNOSTICS
The following diagnostics may be issued on stdout:

DBFOpen(_xbase_file_,"rb+") failed.

Got _count1_ fields, but require _count2_

##AUTHOR
`dbfcreate` is part of shapelib, maintained by Frank Warmerdam. This guide was created by Eduardo Patoo Kanegae and converted to manpage by Johan Van de Wauw. It was further enhanced with the man page written by Joonas Pihlaja (jpihlaja@cc.helsinki.fi).

##BUGS
Field values that are too large to fit in a field are silently truncated from the right. Numeric field values that can't be parsed by `atof`(3) get undefined values.

##SEE ALSO
`dbfcat`(1), `dbfcreate`(1), `dbfdump`(1), `dbfinfo`(1), `shpadd`(1), `shpcat`(1), `shpcentrd`(1), `shpcreate`(1), `shpdump`(1), `shpdxf`(1), `shpfix`(1), `shpinfo`(1), `shpproj`(1), `shprewind`(1), `shptest`(1)

