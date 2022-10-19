shprewind(1) -- validates and resets the winding order of rings
===============================================================

##SYNOPSIS
`shprewind` _in_shp_file_ _out_shp_file_

##DESCRIPTION
Validates and resets the winding order of rings in polygon geometries to match the ordering required by shapefile specification. This is useful for shapefiles having troubles when checked with a 'shpdump -validate'.

Makes a copy of the shapefile _in_shp_file_ to _out_shp_file_ and fixes the orientation of points in the rings of `Polygon`, `PolygonZ`, and `PolygonM` typed shapes to conform to the shapefile specification.  According to the specification, the vertices of outer rings should be oriented clockwise on the _X/Y_ plane, and those of inner rings counterclockwise.

Shapefiles actually consist of two files with the same basename and extensions `.shp` and `.shx` (or `.SHP` and `.SHX`) containing the shape data and shape index respectively.  The files to open are determined by first stripping any filename extension from _in_shp_file_ and attempting to open the files _in_shp_file_`.shp` or _in_shp_file_`.SHP`, and _in_shp_file_`.shx` or _in_shp_file_`.SHX` for the respective data and index files.  The files to create from _out_shp_file_ are determined by stripping any filename extension from _out_shp_file_ and appending `.shp` and `.shx` suffixes for the respective data and index files.

##OPTIONS
 * _in_shp_file_:
 the name of an existing shapefile.

 * _out_shp_file_:
 the name of the new fixed shapefile that will be created.

##EXIT STATUS
 * `0`:
 Successful program execution.

 * `1`:
 Missing _in_shp_file_ or _out_shp_file_ arguments, failed to open shapefile _in_shp_file_ or create shapefile _out_shp_file_.

##DIAGNOSTICS
The following diagnostics may be issued on stdout:

Unable to open:_in_shp_file_

Unable to create:_out_shp_file_

_count_ objects rewound.

##EXAMPLE
`shprewind` _badshapefile_ _newshapefile_

##AUTHOR
`shprewind` is part of shapelib, maintained by Frank Warmerdam. This guide was created by Eduardo Patoo Kanegae and converted to manpage by Johan Van de Wauw. It was further enhanced with the man page written by Joonas Pihlaja (jpihlaja@cc.helsinki.fi).

##BUGS
The implementation assumes that there is at most one outer ring in each shape, that it is the first ring in a shape, and all other rings in a shape are inner rings.  Polygons inside `MultiPatch` shape types aren't rewound.

##SEE ALSO
`dbfadd`(1), `dbfcat`(1), `dbfcreate`(1), `dbfdump`(1), `dbfinfo`(1), `shpadd`(1), `shpcat`(1), `shpcentrd`(1), `shpcreate`(1), `shpdump`(1), `shpdxf`(1), `shpfix`(1), `shpinfo`(1), `shpproj`(1), `shptest`(1)

