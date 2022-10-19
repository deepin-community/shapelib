dbfinfo(1) -- Displays basic information for a given xBase file
===============================================================

##SYNOPSIS
`dbfinfo` _xbase_file_

##DESCRIPTION
Displays basic information for a given xBase file, like number of columns, number of records and type of each column.

##OPTIONS
 * _xbase_file_:
 The name of an existing xBase file.

##EXAMPLE
`dbfinfo` _testbase_

    Info for testbase.dbf
    3 Columns,  1 Records in file
               NAME          string  (20,0)
               AREA           float  (9,3)
              VALUE           float  (9,2)


##AUTHOR
`dbfinfo` is part of shapelib, maintained by Frank Warmerdam. This guide was created by Eduardo Patoo Kanegae and converted to manpage by Johan Van de Wauw.

##SEE ALSO
`dbfadd`(1), `dbfcat`(1), `dbfcreate`(1), `dbfdump`(1), `shpadd`(1), `shpcat`(1), `shpcentrd`(1), `shpcreate`(1), `shpdump`(1), `shpdxf`(1), `shpfix`(1), `shpinfo`(1), `shpproj`(1), `shprewind`(1), `shptest`(1)

