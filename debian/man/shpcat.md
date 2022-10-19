shpcat(1) -- appends the records of a source shapefile
======================================================

##SYNOPSIS
`shpcat` [`-v`] [`-f`] _from_shpfile_ _to_shpfile_

##DESCRIPTION
Appends the content of a source shapefile into a destination shapefile. Both files must be the same shapefile type.

##OPTIONS
 * `-v`:
 verbose mode.

 * `-f`:
 forces data conversion if data field types is not the same at both files or if is there any null value into from_DBFfile.

 * _from_shpfile_:
 source shapefile.

 * _to_shpfile_:
 destination shapefile.

##EXAMPLE
`shpcat` `-v` _shapefile1_ _shapefile2_

##AUTHOR
`shpcat` is part of shapelib, maintained by Frank Warmerdam. This guide was created by Eduardo Patoo Kanegae and converted to manpage by Johan Van de Wauw.

##SEE ALSO
`dbfadd`(1), `dbfcat`(1), `dbfcreate`(1), `dbfdump`(1), `dbfinfo`(1), `shpadd`(1), `shpcentrd`(1), `shpcreate`(1), `shpdump`(1), `shpdxf`(1), `shpfix`(1), `shpinfo`(1), `shpproj`(1), `shprewind`(1), `shptest`(1)

