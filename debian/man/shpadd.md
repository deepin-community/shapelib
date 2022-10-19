shpadd(1) -- append a shape to an ESRI shapefile
================================================

##SYNOPSIS
`shpadd` _shp_file_ [[_x_ _y_] [+]]*

##DESCRIPTION
Appends a shape to the shapefile determined from _shp_file_.  The geometric data of the new shape consists of lists of _X/Y_ points on the command line grouped into _parts_, with points in different parts separated by a plus (`+`) sign. If no points or parts are given then a shape of type NullShape is appended to the shapefile, and otherwise the type of the new shape is determined by the shapefile's header.  See `shpdump`(1) for a description of shape types and how geometric data for parts are interpreted for a specific type.  No geometric restrictions set by the shapefile specification are enforced by `shpadd`(1).

Shapefiles actually consist of two files with the same basename and extensions `.shp` and `.shx` (or `.SHP` and `.SHX`) containing the shape data and shape index respectively.  The files to open are determined by first stripping any filename extension from file and attempting to open the files _shp_file_`.shp` or _shp_file_`.SHP`, and _shp_file_`.shx` or _shp_file_`.SHX` for the respective data and index files.

##OPTIONS
 * _shp_file_:
 the name of an existing shapefile.

 * _x1_ _y1_ _x2_ _y2_ ... _xn_ _yn_:
 the set of x,y coordinates that describes the shape that you wish to add.  Note that you must specify the correct number of parameters for a given type of shapefile. e.g.: for point shapefiles you have to pass 1 pair of XY coordinates and for a polygon shapefile you should pass at least 4 pairs of XY coordinates (where the first and the last point must have the same coordinates).

##EXAMPLE
`shpadd` _testpolygon_ 100000 7000000 250000 6500000 200000 6000000 100000 7000000

assuming that _testpolygon_ is a polygon shapefile, this command line will insert a new shape (a triangle) into testpolygon with the following XY coordinates:

	vertice 0: 100000 7000000 (this will also be the vertice where the shape starts and ends)
	vertice 1: 250000 6500000
	vertice 2: 200000 6000000
	vertice 3: 100000 7000000

##EXIT STATUS
 * `0`:
 Successful program execution.

 * `1`:
 Missing _shp_file_ argument, the shapefile can't be opened, or the program ran out of memory.

##DIAGNOSTICS
The following diagnostics may be issued on stdout:

Unable to open:_shp_file_

Out of memory

##AUTHOR
`shpadd` is part of shapelib, maintained by Frank Warmerdam. This guide was created by Eduardo Patoo Kanegae and converted to manpage by Johan Van de Wauw.

##BUGS
Coordinate values that can't be be parsed by `sscanf`(3) get undefined values.  There's no way to give measure or _Z_ data to vertices in a shape, but those are always set to zero if the shapefile's shape type requires those values.  `MultiPatch` shape types aren't supported.

##SEE ALSO
`dbfadd`(1), `dbfcat`(1), `dbfcreate`(1), `dbfdump`(1), `dbfinfo`(1), `shpcat`(1), `shpcentrd`(1), `shpcreate`(1), `shpdump`(1), `shpdxf`(1), `shpfix`(1), `shpinfo`(1), `shpproj`(1), `shprewind`(1), `shptest`(1)

