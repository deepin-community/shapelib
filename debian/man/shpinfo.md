shpinfo(1) -- Displays basic information for a given shapefile
==============================================================

##SYNOPSIS
`shpinfo` _shapefile_

##DESCRIPTION
Displays basic information for a given shapefile, like shapefile type, number of objects and its extents.

##OPTIONS
 * _shapefile_:
 The name of an existing shapefile.

##EXAMPLE
`shpinfo` _testpolygon_

    Info for testpolygon
    Polygon(5), 1 Records in file
    File Bounds: (         100000,        6000000)
            (         250000,        7000000)

##AUTHOR
`shpinfo` is part of shapelib, maintained by Frank Warmerdam. This guide was created by Eduardo Patoo Kanegae and converted to manpage by Johan Van de Wauw.

##SEE ALSO
`dbfadd`(1), `dbfcat`(1), `dbfcreate`(1), `dbfdump`(1), `dbfinfo`(1), `shpadd`(1), `shpcat`(1), `shpcentrd`(1), `shpcreate`(1), `shpdump`(1), `shpdxf`(1), `shpfix`(1), `shpproj`(1), `shprewind`(1), `shptest`(1)

