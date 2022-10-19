dbfdump(1) -- dumps the content of a xBase file to the terminal
===============================================================

##SYNOPSIS
`dbfdump` [`-h`] [`-r`] [`-m`] _xbase_file_

##DESCRIPTION
Dumps the contents of _xbase_file_ to standard output. The first line contains the field names appearing in _xbase_file_, and each of the following lines contains the field values of a record. Field names and values are padded by spaces to their field widths. Empty fields are printed as the string "(NULL)".

##OPTIONS
 * `-h`:
 output header info (field descriptions).

   Prints the column field definitions before other output. Each field definition consists of a line of the form

   Field: _index_, Type=_type_, Title=`_name_', Width=_width_, Decimals=_precision_

   where _index_ is the zero offset column number of the field; the _type_ indicates the datatype of the field value and is either "Integer", "Real" or "String"; _name_ is the field's name; _width_ is the number of bytes reserved for the field's value; and _precision_ is the number of decimal places of precision for "Real" type fields, and is zero for "Integer" and "String" type fields.

 * `-r`:
 output raw field info, numeric values not reformatted.

   Prints the exact bytes occurring in _xbase_file_ for field values and suppresses printing "(NULL)" for empty values.

 * `-m`:
 output one line per field.

   Prints each record in multiline format separated by empty lines. The first line of a record gives the number of the record in the form

   Records: _record_index_

   where _record_index_ is the zero offset number of the record in the file, and then each field of the record appears on its own line in the format

   _name_: _value_

 * _xbase_file_:
 the name of an existing xBase file.

##EXAMPLE
`dbfdump` `-h` _testbase.dbf_

assuming that _testbase.dbf_ has 1 record (inserted by other example using `dbfadd`), this command line will produce the following output:

	Field 0: Type=String, Title='NAME', Width=20, Decimals=0
	Field 1: Type=Double, Title='AREA', Width=9, Decimals=3
	Field 2: Type=Double, Title='VALUE', Width=9, Decimals=2
	NAME AREA VALUE REGION1 25.656 150.22

##EXIT STATUS
 * `0`:
 Successful program execution.

 * `1`:
 Missing _xbase_file_ argument.

 * `2`:
 Failed to open _xbase_file_.

 * `3`:
 There are no fields in _xbase_file_.

##DIAGNOSTICS
The following diagnostics may be issued on stdout:

DBFOpen(_xbase_file_,"r") failed.

There are no fields in this table!

##AUTHOR
`dbfdump` is part of shapelib, maintained by Frank Warmerdam. This guide was created by Eduardo Patoo Kanegae and converted to manpage by Johan Van de Wauw. It was further enhanced with the man page written by Joonas Pihlaja (jpihlaja@cc.helsinki.fi).

##BUGS
Unless the `-r` option is given, values in numeric fields that overflow the `int` or `double` types of the `C` language are printed as plus or minus a huge number. For integer fields the huge value is `HUGE_VALL` from <stdlib.h> and for real fields it is `HUGE_VALF`.

##SEE ALSO
`dbfadd`(1), `dbfcat`(1), `dbfcreate`(1), `dbfinfo`(1), `shpadd`(1), `shpcat`(1), `shpcentrd`(1), `shpcreate`(1), `shpdump`(1), `shpdxf`(1), `shpfix`(1), `shpinfo`(1), `shpproj`(1), `shprewind`(1), `shptest`(1)

