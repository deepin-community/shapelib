shpsort(1) -- rewrite a shapefile sorted by a field or by the geometry
======================================================================

##SYNOPSIS
`shpsort` _infile_ _outfile_ _field[;...]_ [<(ASCENDING|DESCENDING)[;...]>]

##DESCRIPTION
Rewrite a shapefile sorted by a field or by the geometry.
For polygons, sort by area, for lines sort by length and do nothing for all others.

##OPTIONS
 * _infile_:
 input shapefile

 * _outfile_:
 output shapefile

 * _field[;...]_:
 one or more fields to use for ordering

 * [<(ASCENDING|DESCENDING)[;...]>]:
 sort order

##AUTHOR
`shpsort` is part of shapelib, maintained by Frank Warmerdam.

##SEE ALSO
`dbfadd`(1), `dbfcat`(1), `dbfcreate`(1), `dbfdump`(1), `dbfinfo`(1), `shpcat`(1), `shpcentrd`(1), `shpcreate`(1), `shpdump`(1), `shpdxf`(1), `shpfix`(1), `shpinfo`(1), `shpproj`(1), `shprewind`(1), `shptest`(1)

