dbfcat(1) -- appends the records of a source xBase file
=======================================================

##SYNOPSIS
`dbfcat` [`-v`] [`-f`] _from_DBFfile_ _to_DBFfile_

##DESCRIPTION
Appends the records of a source xBase file into a destiny xBase file. Both files must have the same number of fields.

##OPTIONS
 * `-v`:
 verbose mode.
 * `-f`:
 forces data conversion if data field types is not the same at both files or if is there any null value into _from_DBFfile_.
 * _from_DBFfile_:
 source xBase file.
 * _to_DBFfile_:
 destiny xBase file.

##EXAMPLE
`dbfcat` `-v` _testbase1_ _testbase2_

##AUTHOR
`dbfcat` is part of shapelib, maintained by Frank Warmerdam. This guide was created by Eduardo Patoo Kanegae and converted to manpage by Johan Van de Wauw.

##SEE ALSO
`dbfadd`(1), `dbfcreate`(1), `dbfdump`(1), `dbfinfo`(1), `shpadd`(1), `shpcat`(1), `shpcentrd`(1), `shpcreate`(1), `shpdump`(1), `shpdxf`(1), `shpfix`(1), `shpinfo`(1), `shpproj`(1), `shprewind`(1), `shptest`(1)

